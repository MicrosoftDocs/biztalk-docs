---
title: "Considerations for Working with BAM APIs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dd8ccf63-6989-4ad6-a193-cf3043e9a466
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations for Working with BAM APIs
When using an  "Microsoft.BizTalk.Bam.EventObservation.EventStream" object, such as DirectEventStream, BufferedEventStream, MessagingEventStream, or OrchestrationEventStream, BAM captures milestones such that they are automatically recorded in Coordinated Universal Time (UTC) format (this is also referred to as Greenwich Mean Time). When you send date/times to BAM using the APIs they are received in the format sent with no conversion to UTC format. You should take the following considerations into account when you are developing your BAM solutions:  
  
- Data traced from BizTalk Server is received in UTC format. This could be inconsistent with other data that comes from the event stream.  
  
- If you use the event stream APIs to provide date and time tracking data in local time format, the data in the BAM portal will be incorrect as the expectation is that all times in BAM data are in UTC format.  
  
  If you have existing applications that use local time, and you are now upgrading and planning to use the BAM portal, you must modify your data to make it conform to UTC format. You also need to modify your custom application to convert to UTC format.  
  
## See Also  
 [Implementing BAM Solutions](../core/implementing-bam-solutions.md)