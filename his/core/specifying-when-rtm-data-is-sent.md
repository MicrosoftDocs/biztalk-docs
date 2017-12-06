---
title: "Specifying When RTM Data is Sent1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a989286-9dac-4932-b3c8-ae06d20d063a
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Specifying When RTM Data is Sent
Response times are recorded for a specific logical unit (LU) rather than for a specific 3270 session. If a 3270 session ends and another session of the same or a different 3270 user starts using the same LU, the response time counters include responses from both sessions. To prevent the counters from collecting information from more than one 3270 session, you can reset the RTM counters on the LU before a new session begins. The counters are reset when the host requests the reset or when response time monitor (RTM) data is sent unsolicited by [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)]. Usually when a host requests RTM data the counters are reset at the same time.  
  
 To ensure that RTM data relates only to the current 3270 session, you should select the **End-of-Session** checkbox when configuring RTM parameters for [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)]. Note that the host can override this setting.  
  
## See Also  
 [Defining RTM Thresholds](../core/defining-rtm-thresholds.md)   
 [Indicating Lost RTM Data](../core/indicating-lost-rtm-data.md)