---
title: "External Computer Response Time1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a205b2d7-8922-4f7d-b8fd-f71098506ab7
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# External Computer Response Time
External computer response time is sometimes referred to as end-user response time or end-to-end response time. It is the actual response time that the client application that is running on the computer sees.  
  
 When you are using the "FAT-client" architecture, it includes all processing and network delays incurred to the transaction from the time DCOM call was sent to the TI server until the time the reply for the transaction comes back. For "thin client" application architecture, additional delays are incurred because Internet Information Services (IIS) converts the ASP requests to DCOM calls, and delivers the DCOM replies back to the ASP pages for the client on the intranet or Internet.  
  
## See Also  
 [Major Elements Affecting Overall Performance](../core/major-elements-affecting-overall-performance1.md)