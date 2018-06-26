---
title: "BizTalk ESB Toolkit Message Life Cycle | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c72fdbda-b9ef-431a-8322-56dba98e9eab
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk ESB Toolkit Message Life Cycle
The following is the life cycle of a message that originates from an external system and traverses through the ESB to reach its final destination:  

1. An on-ramp receives the message. Depending on the submitting party or client, the message may or may not contain an itinerary that defines the processing instructions for the message.  

2. ESB pipeline components copy the itinerary (if present in the SOAP header) into the context of the message as promoted properties. If the message is received without an itinerary, a specific pipeline component can be configured to select the appropriate itinerary from a database, depending on message content or context, and then copy the itinerary into the context of the message. For the duration of the lifetime of the message, the itinerary is maintained within the message context.  

3. While still in the pipeline, the itinerary is evaluated and message-based itinerary services can process the message. These itinerary services may transform the message or configure routing endpoints.  

4. The message is published to the Microsoft BizTalk Server Message Box database.  

5. BizTalk Server evaluates the promoted properties of the message and queues the message for one or more subscribers.  

6. The subscriber(s) process the message using typical BizTalk Server mechanisms. A subscriber can be either of the following:  

   -   A BizTalk Server orchestration with a filter configured on a direct-bound receive port  

   -   A dynamic BizTalk Server send port, which is also referred to as an ESB off-ramp. The itinerary determines how the port will be configured to continue processing the message.  

   As an alternative to a message arriving through an itinerary on-ramp, BizTalk Server orchestrations can also publish messages to the Message Box for ESB processing:  

7. A message is created within a BizTalk Server orchestration.  

8. The message's context is populated with the ESB itinerary.  

9. The message is published through a direct-bound port to the Message Box database.
