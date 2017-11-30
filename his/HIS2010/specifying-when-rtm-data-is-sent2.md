---
title: "Specifying When RTM Data is Sent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5883baea-d128-4a5a-b6b2-50952acc19f5
caps.latest.revision: 3
---
# Specifying When RTM Data is Sent
Response times are recorded for a specific logical unit (LU) rather than for a specific 3270 session. If a 3270 session ends and another session of the same or a different 3270 user starts using the same LU, the response time counters include responses from both sessions. To prevent the counters from collecting information from more than one 3270 session, you can reset the RTM counters on the LU before a new session begins. The counters are reset when the host requests the reset or when response time monitor (RTM) data is sent unsolicited by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]. Usually when a host requests RTM data the counters are reset at the same time.  
  
 To ensure that RTM data relates only to the current 3270 session, you should select the **End-of-Session** checkbox when configuring RTM parameters for [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]. Note that the host can override this setting.  
  
## See Also  
 [Defining RTM Thresholds](../HIS2010/defining-rtm-thresholds1.md)   
 [Indicating Lost RTM Data](../HIS2010/indicating-lost-rtm-data2.md)