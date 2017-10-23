---
title: "Large-growing BizTalk Server Database Tables | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f30372f7-ab90-4ebb-9022-ac3ae3309459
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Large-growing BizTalk Server Database Tables
The following table lists the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tables that typically grow the largest. You can use this data to determine where a potential problem may exist.  
  
|Table|Description|Comments|  
|-----------|-----------------|--------------|  
|*HostNameQ*_Suspended table|This table contains a reference to messages in the Spool table that are associated with suspended instances for the particular host. This table is in the BizTalkMsgBoxDb database.|If the *HostNameQ*_Suspended tables have many records, the tables could be containing valid suspended instances that appear in the **Group Hub** page. You can terminate these instances. If these instances do not appear in the **Group Hub**, the instances are probably caching instances or orphaned routing failure reports. When you terminate suspended instances, you clean up the items in this table and their associated rows in the Spool and Instances tables.|  
|*HostNameQ* table|This table contains a reference to messages in the Spool table that are associated with the particular host and are not suspended. This table is in the BizTalkMsgBoxDb database.|If the *HostNameQ* tables have many records, the following kinds of instances may exist:<br /><br /> -   Ready-to-run instances<br />-   Active instances<br />-   Dehydrated instances<br /><br /> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] needs time to "catch up" and process the instances. This table can grow when the incoming rate of processing outpaces the outgoing rate of processing. This scenario can also occur due to large BizTalkDTADb database or SQL Server disk delays.|  
|Spool, Parts, and Fragments tables|These tables store actual message data in the BizTalkMsgBoxDb database.|The Spool, Parts, and Fragments tables having many records imply that there are a large number of messages are currently active, dehydrated, or suspended. Depending on the size, the number of parts, and the fragmentation settings in these tables, a single message may spawn all these tables. Each message has exactly one row in the Spool table and at least one row in the Parts table.|  
|Instances table|This table stores all instances and their current status in the BizTalkMsgBoxDb database.|The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrator should not allow for many suspended instances to remain in the Instances table. Many dehydrated instances should only remain if the business logic requires long-running orchestrations. Remember that one service instance can be associated with many messages in the Spool table.|  
|TrackingData*_x_x* table|This table stores the tracked events in the BizTalkMsgBoxDb database for Tracking Data Decode Service (TDDS) to move the events to the BizTalkDTADb database.|If the TrackingData_*x_x* tables are large, either the TDDS is not running or is not running successfully. If the TDDS is running, review the event logs and the TDDS_FailedTrackingData table in the BizTalkDTADb database for error information.|  
|Tracking_Fragments*x*, Tracking_Parts*x*, Tracking_Spool*x* tables|Two of each of these tables is in the BizTalkMsgBoxDb and BizTalkDTADb databases. One is online, and the other is offline.|The **TrackedMessages_Copy_BizTalkMsgBoxDb** SQL Server Agent job moves tracked message bodies directly to these tables in the BizTalkDTADb database.|  
|dta_ServiceInstances table|This table stores tracked events for service instances in the BizTalkDTADb database.|If this table is large, the BizTalkDTADb database is probably large.|  
|dta_DebugTrace table|This table stores the Orchestration debugger events in the BizTalkDTADb database.|If the dta_DebugTrace table has many records, orchestration shape tracking is being used or was being used. If orchestration debugging is not required for regular operations, disable orchestration shape tracking for all orchestrations. If orchestration shape tracking is already disabled and a backlog exists in the BizTalkMsgBoxDb database, the dta_DebugTrace table may continue to grow because TDDS continues to move this data into the dta_DebugTrace table.<br /><br /> To control the size of the BizTalkDTADb tracking database, you may choose to disable global tracking. For more information see [How to Turn Off Global Tracking](http://go.microsoft.com/fwlink/p/?LinkId=153687). For more information about tracking database sizing guidelines, see [Tracking Database Sizing Guidelines](http://go.microsoft.com/fwlink/p/?LinkId=153688).|  
|dta_MessageInOutEvents table|This table stores tracked event messages in the BizTalkDTADb database. These tracked event messages include message context information.|If the dta_DebugTrace table and the dta_MessageInOutEvents table in the BizTalkTrackingDb database are too large, you can truncate the tables manually after you stop the tracking host. For instructions on how to truncate the tables, follow the procedures under the section "dta_DebugTrace table" of Microsoft Knowledge Base article 952555, [How to maintain and troubleshoot BizTalk Server databases](http://go.microsoft.com/fwlink/p/?LinkId=158847).|  
|dta_ServiceInstanceExceptions table|This table stores error information for any suspended service instance in the BizTalkDTADb database.|The dta_ServiceInstanceExceptions table typically becomes large in an environment that regularly has suspended instances.|
