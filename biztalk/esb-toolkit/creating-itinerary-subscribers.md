---
title: "Creating Itinerary Subscribers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84a76aeb-8d40-490a-8ae6-7abfdd2d2573
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Itinerary Subscribers
[!INCLUDE[prague](../includes/prague-md.md)] automatically publishes messages arriving through a receive pipeline to the Message Box database; this makes the messages ready for pick-up by the relevant subscriber. This decoupled approach is the preferred way to develop BizTalk solutions because it provides maximum flexibility, scales well, and uses the publish-subscribe mechanism.  
  
 There are two ways to create an itinerary service subscriber:  
  
-   [Using a Send Port as an Itinerary Service Subscriber](../esb-toolkit/using-a-send-port-as-an-itinerary-service-subscriber.md)  
  
-   [Using an Orchestration as an Itinerary Service Subscriber](../esb-toolkit/using-an-orchestration-as-an-itinerary-service-subscriber.md)