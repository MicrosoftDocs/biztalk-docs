---
title: "Itinerary-Based Routing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28028721-798c-4302-a532-d863ed8ea88b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Itinerary-Based Routing
One of the core features of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is the provision of itinerary-based routing that simplifies the development of enterprise-level messaging applications and reduces the costs of maintaining a large number of static send ports and receive locations.  
  
 An itinerary consists of the list of services to execute (which can contain routing, transformation, and custom services) and the configuration information required to resolve the metadata necessary to execute each of these services. For example, one stage of the itinerary may be a routing service; the resolution instructions associated with this service may instruct the service to perform a Universal Description, Discovery, and Integration (UDDI) or Business Rules Engine (BRE) lookup for information about a specific target endpoint to which it will route the message.  
  
 Itineraries can be attached to an inbound message in the following ways:  
  
- The message submitted by a client does not contain any itinerary-related data. The receiving pipeline resolves, retrieves, and attaches the appropriate itinerary based on message content or context.  
  
- The message submitted by a client can contain a SOAP header that defines the itinerary reference data, which contains the itinerary name and version, as well as a unique identifier for Business Activity Monitoring (BAM) tracking. The receiving pipeline evaluates this information and retrieves the appropriate itinerary from the ESBItineraryDb database.  
  
- The message submitted by a client can have an itinerary SOAP header, which contains the entire content of the itinerary. This design is not recommended and should be used only for testing purposes.  
  
  After an itinerary is resolved for an inbound message, the receive pipeline promotes the itinerary data to the message context, thereby making the properties available to be accessed by any Microsoft BizTalk Server component that subscribes to this message. BizTalk Server components can obtain details of the current itinerary step, complete the required processing, and/or advance the itinerary to the next step. This causes the next service in the itinerary to process the message, according to the publish-subscribe functionality of BizTalk Server.  
  
  For information about the ESB dynamic resolution mechanism, transformations, itinerary processing, and message creation, see [Key Scenarios and Development Tasks](../esb-toolkit/key-scenarios-and-development-tasks.md).