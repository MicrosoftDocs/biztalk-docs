---
description: "Learn more about: Specifying When RTM Data is Sent"
title: "Specifying When RTM Data is Sent1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Specifying When RTM Data is Sent
Response times are recorded for a specific logical unit (LU) rather than for a specific 3270 session. If a 3270 session ends and another session of the same or a different 3270 user starts using the same LU, the response time counters include responses from both sessions. To prevent the counters from collecting information from more than one 3270 session, you can reset the RTM counters on the LU before a new session begins. The counters are reset when the host requests the reset or when response time monitor (RTM) data is sent unsolicited by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]. Usually when a host requests RTM data the counters are reset at the same time.  
  
 To ensure that RTM data relates only to the current 3270 session, you should select the **End-of-Session** checkbox when configuring RTM parameters for [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]. Note that the host can override this setting.  
  
## See Also  
 [Defining RTM Thresholds](../core/defining-rtm-thresholds2.md)   
 [Indicating Lost RTM Data](../core/indicating-lost-rtm-data1.md)
