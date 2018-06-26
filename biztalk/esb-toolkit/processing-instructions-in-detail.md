---
title: "Processing Instructions in Detail | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed5d92fb-d53b-49a2-b2c7-8558708d6554
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Processing Instructions in Detail
This topic describes the format and structure of the System-Properties.xsd property schema, which defines several context properties required for itinerary processing. These properties are promoted when a message is received and processed through BizTalk Server pipelines; because they are promoted properties, they are accessible to BizTalk Server components. The following properties are defined in the System-Properties.xsd property schema:  
  
- **ItineraryHeader.** This property contains all the itinerary information and a list of itinerary services to be invoked through a sequence of itinerary steps. The Itinerary API uses this property internally.  
  
- **ServiceName.** This property contains the name of the current itinerary service to process.  
  
- **ServiceState.** This property contains the state of the current itinerary service: **Pending**, **Complete**, or **Active**. All services subscribe to an itinerary step that contains a **ServiceState** value of **Pending**.  
  
- **ServiceType.** This property defines the type of the itinerary step (**Messaging** or **Orchestration**).  
  
- **IsRequestResponse.** This property defines the messaging type (one-way or request-response).  
  
  The Itinerary service executes itinerary steps in one of two ways, depending on the value of the **ServiceType** property:  
  
- Itinerary pipeline components execute all itinerary steps with a **ServiceType** property of **Messaging**. Developers can extend this process using a custom pipeline and the Itinerary API.  
  
- When the **ServiceType** property is **Orchestration**, an orchestration, activated by a subscription to itinerary context properties, executes the itinerary step.  
  
  When an Itinerary service processes an itinerary step, the service is responsible for advancing the itinerary and dispatching the message with a new itinerary context for further processing using the publish-subscribe functionality of BizTalk Server. An itinerary service has full control of the itinerary in the message context and can advance to the appropriate step based on its internal logic and the message content.  
  
  The itinerary processing mechanism supports the combination of messaging and orchestration itinerary steps within a single itinerary. Developers can also define custom itinerary services and configure custom itinerary steps.  
  
  For more information about itineraries, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).  
  
  For more information about custom itinerary services and custom itinerary steps, see [Creating a Custom Itinerary Service](../esb-toolkit/creating-a-custom-itinerary-service.md).