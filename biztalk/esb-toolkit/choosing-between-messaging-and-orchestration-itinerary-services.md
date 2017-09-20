---
title: "Choosing Between Messaging and Orchestration Itinerary Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 694f929a-c830-4906-8e97-4fbd50e70133
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Choosing Between Messaging and Orchestration Itinerary Services
Itinerary services can be configured to occur in either the messaging subsystem or the orchestration subsystem of [!INCLUDE[prague](../includes/prague-md.md)]. These ESB itinerary messaging services are configured to process the message and may be executed in a BizTalk Server pipeline (on-ramp or off-ramp). This option enables the developer to define exactly where in the pipeline the service will execute. Naturally, services configured to process in the orchestration subsystem will be executed in a BizTalk orchestration.  
  
## ESB Itinerary Messaging Services  
 When a message is being processed in a BizTalk Server pipeline, using ESB itinerary messaging services reduces message latency. By implementing back-to-back services in a single pipeline, it is possible to transform a message multiple times and route the message to its endpoints with only a single persistence to the Message Box database. Additionally, messaging-based processing eliminates the additional resource cost of orchestration processing. Generally speaking, messaging-based processing is less resource intensive and provides faster processing than orchestration-based processing. In pipelines, the ESB Dispatcher and ESB Dispatcher Disassemble pipeline components provided by [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] act as message interceptors and execute messaging-based itinerary services, whether it is a routing, transformation, or a custom service. For more information about configuring these components, see [The ESB Dispatcher Component](../esb-toolkit/the-esb-dispatcher-component.md) and [The ESB Dispatcher Disassemble Component](../esb-toolkit/the-esb-dispatcher-disassemble-component.md).  
  
## ESB Itinerary Orchestration Services  
 If dynamic routing must occur between or after orchestration processes, use orchestration-based processing for the itinerary service. By default, the orchestration-based services receive the message as an XML document. The Routing orchestration uses the Resolver Manager to attempt to resolve the endpoints identified in the itinerary. The Adapter Manager uses the response from the Resolver Manager to promote the endpoint details into the message context, and the message is published to the Message Box database using a direct-bound logical port. At this point, regular BizTalk routing occurs, and the dynamic send port is configured using the message's promoted properties.  
  
 The included Itinerary Service orchestration provides a good starting point for creating custom orchestration-based itinerary services. For more information about creating custom itinerary services, see [Modifying and Extending the BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).