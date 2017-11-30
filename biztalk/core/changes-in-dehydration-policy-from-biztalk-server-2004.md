---
title: "Changes in Dehydration Policy from BizTalk Server 2004 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c760bffe-5f64-4eb2-bc23-89d7c9310f39
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Changes in Dehydration Policy from BizTalk Server 2004
BizTalk Server dehydration policy has changed from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to BizTalk Server. The explanation for the difference between [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] and BizTalk Server can be summarized by the following Boolean that determines dehydration in [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] (true = dehydrate)  
  
```  
Dehydrate = (WaitingHistory == -1 OR WaitingHistory > TestThreshold)  
```  
  
 Dehydration policy for BizTalk Server has changed in this minor way. BizTalk Server always dehydrates at a receive/delay/listen if there is a wait longer than 2***MaxThreshold**.