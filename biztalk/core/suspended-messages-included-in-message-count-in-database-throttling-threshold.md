---
title: "Suspended Messages are Included in the Message Count in Database Throttling Threshold | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9eb708bb-6d6d-4494-8b8d-67aa44800a20
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Suspended Messages are Included in the Message Count in Database Throttling Threshold
By default the host **Message count in DB** throttling threshold is set to a value of 50,000, which will trigger a throttling condition under the following circumstances:  
  
- The total number of messages published by the host instance to the work, state, and suspended queues of the subscribing hosts exceeds 50,000.  
  
- The number of messages in the spool table or the tracking tables exceeds 500,000 messages.  
  
  Since suspended messages are included in the **Message count in DB** calculation, throttling of message publishing can occur even if the BizTalk server is experiencing low or no load.  
  
## Recommendations  
  
-   If you anticipate that you may have a large number of suspended messages, consider increasing the default value for the **Message count in DB** threshold taking into consideration the space requirements of the SQL server that contains the BizTalk databases. Also consider increasing the **Spool multiplier** and **Tracking data multiplier** values to allow additional backlog in the Spool table.  
  
     For more information about these values, see [How to Modify Resource Based Throttling Settings](../core/how-to-modify-resource-based-throttling-settings.md).  
  
-   Use the **Message publishing throttling state** Performance Monitor counter associated with **BizTalk:MessageAgent** performance object category to measure the current throttling state. If this counter returns a value of 6, then check for suspended instances and terminate or resume suspended instances as needed.  
  
     For more information about the host throttling performance counters, see [Host Throttling Performance Counters](../core/host-throttling-performance-counters.md).  
  
## See Also  
 [Throttling Design Recommendations](../core/throttling-design-recommendations.md)