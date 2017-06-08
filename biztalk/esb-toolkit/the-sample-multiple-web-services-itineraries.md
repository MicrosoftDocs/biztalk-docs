---
title: "The Sample Multiple Web Services Itineraries | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f67a4c6-b547-4261-ab3f-db78603ac588
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Sample Multiple Web Services Itineraries
The following table lists all the predefined itinerary files included with the Multiple Web Services sample. These are located in the \Source\Samples\MultipleWebServices\Itineraries folder.  
  
|File name|Description|  
|---------------|-----------------|  
|OneWayMessagingMultipleServices.xml|This one-way itinerary transforms an NAOrderDoc message to a CNOrderDoc message and then routes it to the Candian Order Service using the off-ramp DynamicResolutionSolicitResp. The response is then transformed to the CNOrderDoc message using the messaging-based transform service and then it is routed again to the Canadian Order Service using the off-ramp DynamicResolutionSolicitResp. The response returned is routed to the Source\Samples\DynamicResolution\Test\Filedrop\Out folder using the routing service.|  
|TwoWayMessagingMultipleServices.xml|This two-way itinerary transforms an NAOrderDoc message to a CNOrderDoc message and then routes it to the Canadian Order Service. It then takes the response from the Canadian Order Service, transforms it to a CNOrderDoc message, and then routes it again to the Canadian Order Service. The result is then returned to the caller. All transformation and routing takes place through messaging services. Both off-ramps use the DynamicResolutionSolicitRespForwarder send port.|  
|TwoWayMessagingOrchestrationMultipleServices.xml|This two-way itinerary uses messaging services to transform an NAOrderDoc message to a CNOrderDoc message, and then it routes that message to the Canadian Order Service using the DynamicResolutionSolicitRespForwarder send port. The response is transformed using the orchestration-based implementation of the transform service, and then it is passed to the custom Microsoft.Practices.ESB.Routing.TwoWay orchestration-based itinerary service provided as part of the sample. This service sends a message to the Web service specified by the associated resolver (in this case, the Canadian Order Service), and then it receives and returns the response from the service. This response is then sent back to the caller.|  
|TwoWayOrchestrationsMultipleServices.xml|This two-way itinerary uses a messaging service to transform an NAOrderDoc message to a CNOrderDoc message, and then it uses the Microsoft.Practices.ESB.Routing.TwoWay orchestration to route that message to the Canadian Order Service and return the result. The message is then transformed back to a CNOrderDoc message using the orchestration-based transform service; after that, it is sent back to the Canadian Order Service using the Microsoft.Practices.ESB.Routing.TwoWay orchestration-based itinerary service. The result is then returned to the caller.|  
|TwoWay-Partial-Selector-Required.xml|This two way itinerary uses a messaging service to route an NAOrderDoc message to the Canadian Order Service through the DynamicResolutionSolicitResp off-ramp. The NAOrderDoc is transformed to CNOrderDoc using the messaging-based transform service and Canadian service called. The response is then returned back to caller.|