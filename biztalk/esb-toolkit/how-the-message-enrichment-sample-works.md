---
title: "How the Message Enrichment Sample Works | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1188c1c9-b133-4438-b41c-ea6cffcf40fd
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How the Message Enrichment Sample Works
 The Message Enrichment sample demonstrates that it is possible to encapsulate an integration pattern as a generic reusable service. In this case the sample implements the Content Enricher pattern. The Content Enricher pattern generally involves using a transform to prepare a message for transmission to an external service in order to lookup information, and then another transform to incorporate the response into a new message which also contains data from the original message. In order to implement the pattern in a generic fashion, the Message Enrichment sample provides an orchestration-based itinerary service that can use up to two resolvers to configure enrichment of a message using information from an external source.
  
 The first resolver must return routing information; it can also return transform information alongside it. If specified, the transform is applied to the incoming message before being routed to the location specified by the resolver. In the provided sample itinerary, the WCF-Custom adapter provider is used to execute a SQL stored procedure within the GlobalBankESB database named GetOrderDetails and return the result.  
  
 Optionally, a second resolver can be included. If provided, the second resolver must include transformation information. This transform will be given the original message and the result, returned by whichever data source was contacted, as input. In the sample itinerary, a map is referenced that uses a table looping functoid to pull information out of the original message and the result of the stored procedure and include it inside the resulting InventoryOrder message.
