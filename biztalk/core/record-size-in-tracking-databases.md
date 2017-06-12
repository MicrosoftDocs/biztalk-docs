---
title: "Record Size in Tracking Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking database, database size"
ms.assetid: be7a891b-2674-49a3-a8e0-6aa11a918bf2
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Record Size in Tracking Databases
To help you plan your hardware requirements for BizTalk, the following table shows the expected record size for various event records in the Tracking database.  
  
|Action Type|Size|Notes|  
|-----------------|----------|-----------|  
|Deploying a Service|1864 + Symbolic Information Size|Symbolic Information depends on the size of the orchestration. For example, an orchestration that receives one message and sends one message out with 2 shapes in it takes approximately 4000 bytes.|  
|Started and Successfully Completed Service Instance|Normally 252 bytes.<br /><br /> Extreme cases, can reach 735 bytes.||  
|Started and Failed/Exception Met Service Instance|Normally 252 bytes + error information.<br /><br /> Extreme cases can reach 735 bytes + error information.|Error information is the text data returned by a BizTalk or user component. Ranges from 100 bytes to 2 KB.|  
|Start/End of a Shape In an Orchestration|120 bytes each.||  
|Message In/Out Events|Minimum 162 bytes.<br /><br /> First time message is seen it is 202 bytes + Message Property (if tracked)<br /><br /> Extreme cases can reach 2930 bytes.|You can safely assume that the average is 182 bytes if there is no message property tracking.|  
|Message Property Size|40 to 288 bytes if DTA recognizes this tracking property.<br /><br /> Add up to 268 bytes for tracking the property the first time.||  
  
## See Also  
 [What is Message Tracking?](../core/what-is-message-tracking.md)   
 [Management and Tracking Architecture](../core/management-and-tracking-architecture.md)