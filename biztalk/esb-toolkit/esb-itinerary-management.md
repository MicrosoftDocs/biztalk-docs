---
title: "ESB Itinerary Management | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f78240de-34da-4751-aceb-b69d81403124
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ESB Itinerary Management
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] offers two distinct options for ESB itinerary management: centralized and decentralized. This section discusses benefits and risks for each of these options.  
  
## Decentralized ESB Policy Management  
 In this scenario, the ESB client application provides the content of the ESB itinerary as an attachment for each submitted message to the ESB. The message contains a SOAP header with the itinerary contents; when a pipeline component receives the message, it decodes the message, and then it promotes the itinerary to the message context for further routing. Although this design provides the opportunity to easily implement a Routing Slip pattern, fully allowing the client to control the flow of a message presents the following challenges:  
  
- By allowing the client to determine which processes should be applied to a message, the details of available processes from which to choose are transparent to the ESB client application. This practice could potentially expose sensitive information from ESB itinerary to the client.  
  
- In addition to the potential security concerns, allowing the client to manage the itineraries for being submitted with each message does not enforce ESB itinerary as policy unless it is implemented for a specific client. Therefore, costs of change management for enforcing a new version of the itinerary are extremely high and will increase for each new specific type of a trusted client application.  
  
- By allowing the client to pass the entire itinerary with the submitted message, the client should always be located within the trusted subsystem; otherwise, the ESB itinerary could potentially specify malicious processing instructions that are no longer valid.  
  
  [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports processing itineraries submitted by the client; however, this option should only be used for backward compatibility and testing purposes.  
  
  For more information about enabling client-side itineraries, see [Using a Pipeline Component to Read an Itinerary](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md).  
  
## Centralized ESB Policy Management  
 There are potential security and synchronization concerns inherent with allowing a client to submit messages with itineraries attached, so the best practice is to manage ESB itineraries in a central repository implemented as a SQL database and included in [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] for this purpose. By deploying itineraries to a central location, ESB itinerary policies can be easily managed and modified without the need to implement dramatic client-side changes, and the organization can control the processing of messages without exposing potentially sensitive information to the client.  
  
 Specialized pipeline components are provided to determine the appropriate ESB itinerary to attach to an inbound message. This approach provides two distinct options for submitting a message for itinerary-based routing:  
  
-   Using the first option, the client application can still indicate a distinct ESB itinerary by providing ESB itinerary reference information in the SOAP header along with request message, instead of submitting a complete itinerary. This information includes ESB itinerary name and optional version. In this scenario, clients can still specify how message can be routed, but there is no risk of policy synchronization errors or security compromises by exposing content of the ESB itinerary to client applications.  
  
-   The second option is to configure the ESB on-ramp to automatically determine the appropriate ESB itinerary, based on the content or context of the message, without requiring any header information from the submitting client. This scenario enables the organization to control the flow of a submitted message and eliminates the need for the client to be aware of how the message is being routed.