---
title: "Using a Pipeline Component to Select an Existing Itinerary | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b93c5cb6-071f-485d-b0bb-22f95bafa3d0
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using a Pipeline Component to Select an Existing Itinerary
## ESB Itinerary Selector Pipeline Component  
 Messages submitted using generic itinerary on-ramps are submitted without an itinerary header. To resolve the appropriate itinerary and attach it to the incoming message, the on-ramp must provide a mechanism that can be configured to access itineraries from a central repository.  

 The ESB Itinerary Selector pipeline component uses a resolver connection string, in conjunction with specialized resolvers, to resolve the content of a server-side itinerary stored in a central repository (by default, SQL Server).  

 When the ESB Itinerary Selector pipeline component is used in WCF on-ramps in conjunction with the ITINERARY-STATIC resolver, the name and version of the itinerary requested by the client (as represented in the SOAP header) is retrieved from the message context and is used to select the appropriate itinerary.  

 By default, the ESB Itinerary Selector pipeline component resides in the following pipelines:  

- ItinerarySelectReceive  

- ItinerarySelectReceivePassthrough  

- ItinerarySelectReceiveXml  

- ItinerarySelectSendReceive  

  The following sections describe the steps performed by each component.  

## ESB Itinerary Selector Pipeline Component Processing Steps  
 The ESB Itinerary Selector pipeline component executes the following steps:  

- The submitting party submits a message for processing. The Itinerary Selector component uses a resolver specified as a property connection string, configured by the developer, to determine and select the appropriate itinerary from the itinerary store, based on message content or context.  

- It validates the itinerary and sets specific properties to preset default values if they are null in the itinerary; for example:  

  - If Service count is less than 1, the component throws an exception.  

  - The component sets the itinerary root attributes using the values for the Service count, the identifier (**Uuid**), the start time (**BeginTime**), and whether this is a one-way or two-way request (**IsRequestResponse**).  

  - The component validates the services, sets the identifiers, sets the current service instance (the service to process next), and validates any associated resolvers.  

  - The component sets the Microsoft BizTalk Server segment of the itinerary using the following properties:  

    -   **correlationToken**  

    -   **reqRespTransmitPipelineID**  

    -   **interchangeId**  

    -   **receiveInstanceId**  

    -   **epmRRCorrelationToken**  

  - The component writes the modified itinerary to the BizTalk message context properties listed in the following table using the properties defined in the System-Properties.xsd schema.  


    |                                           Properties                                           |
    |------------------------------------------------------------------------------------------------|
    |                                   **Name = ItineraryHeader**                                   |
    | **Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties** |


  - The component promotes the four BizTalk context properties listed in the following table using the values defined in the System-Properties.xsd schema.  

    |Property|Value|  
    |--------------|-----------|  
    |**ServiceName**|The name of the current service instance defined in the itinerary.|  
    |**ServiceType**|Set to either **Orchestration** or **Messaging**.|  
    |**IsRequestResponse**|Set to either **True** or **False**.|  
    |**ServiceState**|Set to **Pending**.|  

## ESB Dispatcher Pipeline Component Process Steps  
 The ESB Dispatcher pipeline component executes the following steps:  

-   It manages the execution of any itinerary steps of type **Messaging** and advances the itinerary. The ESB Dispatcher component is location-aware and executes logic based on its location in the messaging processing cycle, which could be **Receive Inbound**, **Send Transmit**, **Send Inbound**, or **Receive Outbound**. The ESB Dispatcher pipeline component invokes ESB itinerary messaging services specified in the Esb.config file. By default, the configuration properties of this component for routing and transformation are associated with the following services:  

    -   **Microsoft.Practices.ESB.Services.Transform**. This service executes BizTalk maps against the payload of an inbound message. The service validates transform requirements and updates the BizTalk context properties that contain the document specification name and the message type. The ESB Dispatcher executes this service only if this is the name of the transform service as it appears in the corresponding property of the ESB Dispatcher pipeline component.  

    -   **Microsoft.Practices.ESB.Services.Routing.** This service uses the Resolver and Adapter Provider Framework to set the appropriate endpoint routing information. The ESB Dispatcher executes this service only if this is the name of the routing service as it appears in the corresponding property of the ESB Dispatcher pipeline component.