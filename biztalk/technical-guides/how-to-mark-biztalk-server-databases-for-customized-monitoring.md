---
title: "How to Mark BizTalk Server Databases for Customized Monitoring | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cfbdc73d-a108-42ee-a5d8-401d5bfe5e7d
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Mark BizTalk Server Databases for Customized Monitoring
If you have installed the Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack, you can customize the way [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are monitored. This ensures that the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack monitors the following [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases:  
  
-   BAM Archive (BAMArchive) database  
  
-   BAM Primary Import (BAMPrimaryImport) database  
  
-   BAM Star Schema (BAMStarSchema) database  
  
-   BizTalk Tracking (BizTalkDTADb) database  
  
-   BizTalk Management (BizTalkMgmtDb) database  
  
-   BizTalk MessageBox (BizTalkMsgBoxDb) database  
  
-   Rule Engine (BizTalkRuleEngineDb) database  
  
-   Enterprise Single Sign-On (SSODB) database  
  
> [!NOTE]
>  You must be logged on as a member of the Operations Manager Advanced Operator role or [!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)] Management Group.  
  
### To mark BizTalk Server databases for customized monitoring  
  
1. Click **Start**, click **All Programs**, click **System Center Operations Manager 2007**, and then click **Operations Console**.  
  
2. In the Operations console, click the **Authoring** button.  
  
3. In the **Authoring** pane, expand **Management Pack Objects**, and then click **Object Discoveries**.  
  
4. To locate a discovery for SQL Server, on the Operations console toolbar click **Find**, and in the **Look for** text box enter **SQL 2008** to search for SQL Server 2008.  
  
5. Under the **Discovered Type: SQL 2008 DB** category, select **Discover Databases for a Database Engine**.  
  
6. On the Operations console toolbar, click **Overrides** and then point to **Override the Object Discovery**. You can choose to override the discovery for objects of a specific type or for all objects within a group. After you choose which group of object type to override, the **Override Properties** dialog box opens.  
  
   > [!NOTE]  
   >  If the **Overrides** button is not available, make sure you have selected a monitor and not a container object in the Monitors pane.  
  
7. Select the check box in the **Override** column next to the **Exclude List** parameter, and in the **Override Value** column, type the name of the database that you want to exclude from monitoring. Make sure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases that you want to monitor are not listed in the **Override Value** column.  
  
   > [!TIP]  
   >  You can use the modified object discoveries to create a new management pack. At the bottom of the pane, the **Select destination management pack** drop-down shows a default value of **Default Management Pack**. Click **New** to create a new management pack using the modified object discoveries.  
  
## See Also  
 [Monitoring SQL Servers](../technical-guides/monitoring-sql-servers.md)