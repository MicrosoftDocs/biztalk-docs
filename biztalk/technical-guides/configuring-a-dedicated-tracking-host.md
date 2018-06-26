---
title: "Configuring a Dedicated Tracking Host | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f997bcc2-08fd-4e9a-ba44-542ec8460d6d
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring a Dedicated Tracking Host
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is optimized for throughput, so the main orchestration and messaging engines do not actually move events or messages directly to the BizTalk Tracking (DTA) or Business Activity Monitoring (BAM) databases, since this would divert these engines from their primary job of executing business processes. Instead, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] leaves the events and messages in the MessageBox database and marks them as requiring a move to the BizTalk Tracking or BAM databases. A background process (the tracking host) then moves the events to the BizTalk Tracking and BAM databases, while a SQL Server Agent job copies tracked messages to the BizTalk Tracking database.  
  
## Advantages of Using a Dedicated Tracking Host  
 A BizTalk Host that hosts tracking is responsible for moving the DTA and BAM tracking data from the MessageBox database to the BizTalk Tracking (DTA) and BAM Primary Import databases. This movement of tracking data has an impact on the performance of other BizTalk artifacts that are running in the same host that is hosting tracking. Thus, you should use a dedicated host that does nothing but host tracking.  
  
 Using a dedicated tracking host also allows you to stop other BizTalk hosts without interfering with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tracking. The movement of tracking data out of the MessageBox database is critical for a healthy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system. If the BizTalk Host responsible for moving tracking data in the BizTalk group is stopped, the Tracking Data Decode service will not run. The impact of this is as follows:  
  
- HAT tracking data will not be moved from the MessageBox database to the BizTalk Tracking database.  
  
- BAM tracking data will not be moved from the MessageBox database to the BAM Primary Import database.  
  
- Because data is not moved, it cannot be deleted from the MessageBox database.  
  
- When the Tracking Data Decode service is stopped, tracking interceptors will still run and write tracking data to the MessageBox database. If the data is not moved, this will cause the MessageBox database to become bloated, which will affect performance over time. Even if custom properties are not tracked or BAM profiles are not set up, by default some data is tracked (such as pipeline receive / send events and orchestration events). If you do not want to run the Tracking Data Decode service, turn off all tracking so that no interceptors save data to the database. To disable global tracking, see [How to Turn Off Global Tracking](http://go.microsoft.com/fwlink/?LinkId=154193) (<http://go.microsoft.com/fwlink/?LinkId=154193>) Use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to selectively disable tracking events.  
  
## Optimizing Performance for a Dedicated Tracking Host  
 This host should be run on at least two computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (for redundancy in case one fails). For optimal performance, you should have at least one tracking host instance per MessageBox database. The actual number of tracking host instances should be N + 1, where N = the number of MessageBox databases. The "+ 1" is for redundancy. There is no benefit to adding more than that, because only one tracking host instance can move data for a specific MessageBox database. As a result, locking should never be an issue. The one additional tracking host instance is added for fault tolerance; if one of the tracking host instances fails, the additional instance will assume the duties of the failed instance.  
  
 A tracking host instance moves tracking data for specific MessageBox databases, but there will never be more than one tracking host instance moving data for a specific MessageBox database. For example, if you have three MessageBox databases, and only two tracking host instances, then one of the host instances needs to move data for two of the MessageBox databases. Adding a third tracking host instance distributes the tracking host work to another computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. In this scenario, adding a fourth tracking host instance would not distribute any more tracking host work, but would provide an extra tracking host instance for fault tolerance.  
  
 For more information about the BAM Event Bus service, see the following topics in BizTalk Server Help:  
  
-   [Managing the BAM Event Bus Service](http://go.microsoft.com/fwlink/?LinkId=154194) (http://go.microsoft.com/fwlink/?LinkId=154194)  
  
-   [Creating Instances of the BAM Event Bus Service](http://go.microsoft.com/fwlink/?LinkId=154195) (http://go.microsoft.com/fwlink/?LinkId=154195)  
  
## Configuring a Dedicated Tracking Host  
 To perform the procedure in this section, you must have the following user rights for modifying host properties to allow host tracking:  
  
- You must be a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
- You must have the following rights in SQL Server:  
  
  -   You must be either a SQL Server administrator or a member of the *db_owner* or *db_securityadmin* SQL Server database roles in the BizTalk Tracking database (BizTalk DTADb), MessageBox databases (BizTalkMsgBoxDb), and the BAM Primary Import database (BAMPrimaryImport).  
  
  -   You must be a member of the sysadmin SQL Server role on all the computers where there are MessageBox databases, or a member of the *db_owner* or *db_ddladmin* SQL Server role for all the MessageBox databases.  
  
#### To enable host tracking  
  
1. Click **Start**, click **Programs**, click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand the BizTalk group, click **Platform Settings**, and then click **Hosts**.  
  
3. In the details pane, right-click the host that you want to modify, and then click **Properties**.  
  
4. In the **Host Properties** dialog box, on the **General** tab, select or clear **Options - Allow Host Tracking**, and then click **OK**.  
  
    Select this check box to indicate that the host loads the BizTalk Tracking component to process health monitoring and business data. If you select this check box, the current host will have read/write access to the tracking tables in the MessageBox database, as well as to the Tracking database. Accordingly, any objects running in this host will also have read/write access to these databases.  
  
    If you clear the check box, the host will have only write access to the tracking tables in the MessageBox database and will not have access to the Tracking database.  
  
## See Also  
 [Checklist: Configuring BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)