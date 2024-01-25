---
description: "Learn more about: Tracking Database Sizing Guidelines"
title: "Tracking Database Sizing Guidelines"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Tracking Database Sizing Guidelines
This section describes sizing considerations for the BizTalk Tracking (BizTalkDTADb) database in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. It explains how to use equations and message variables to determine how large the BizTalk Tracking database will become over a given period of time, and provides specific examples of how to apply the equations. This provides the rough co-relation between BizTalk messages, tracking settings and the tracking database size. It does not take into account other SQL Server factors such as index size in the tracking tables; you may want to consider reasonable multipliers to account for those factors.  
  
## In This Section  
  
-   [Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md)  
  
-   [Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md)  
  
-   [Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)  
  
-   [Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)  
  
-   [Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)  
  
-   [Scenario 4: Sizing the Tracking Database for all Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)  
  
## See Also  
 [Record Size in Tracking Databases](../core/record-size-in-tracking-databases.md)   
 [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md)
