---
title: "How to Connect to an Existing Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.procedure.connecttogroup"
helpviewer_keywords: 
  - "groups, existing"
  - "groups, connecting"
  - "managing [groups], connecting"
ms.assetid: 1eedbcd5-f3f1-4da5-b91c-67377131f889
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Connect to an Existing Group
You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console on any computer in your enterprise to remotely manage one or more BizTalk Server groups within your enterprise, as long as these groups are located on computers within the same domain or within trusted domains.  
  
 The BizTalk Server Administration node in the BizTalk Server Administration console is the highest-level node for all BizTalk groups, and is the level that you use when adding an existing BizTalk Server group to the BizTalk Server Administration console. When you add a group, you must specify an existing server and BizTalk Management database to which you want to connect.  
  
## Prerequisites  
 To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group or as a member of the BizTalk Server Administrators group.  
  
### To connect to an existing group  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, right-click **BizTalk Server Administration**, and then click **Connect to Existing Group**.  
  
3. In the **Connect to Existing BizTalk Server Configuration Database** dialog box, in the **SQL Server name** drop-down list box, select the name of the Microsoft SQL Server instance that hosts the BizTalk Management database (also referred to as the Configuration database). When you select the instance of SQL Server, BizTalk Server automatically attempts to detect BizTalk Server databases on that computer.  
  
4. In the **Database name** drop-down list box, select the BizTalk Server Management database (**BizTalkMgmtDb**) to which you want to connect, and then click **OK**.  
  
    The BizTalk Server Administration console adds the BizTalk Server group to the console tree.  
  
   > [!NOTE]
   >  If the BizTalk Server Management database is housed on a SQL Server cluster and the cluster is in the process of failing over then you may receive an error similar to the following when you attempt to connect to the Management database:  
   >   
   >  Failed to load Group [\<servername\>:\<management database\>] data providers.  
   >   
   >  And  
   >   
   >  ADDITIONAL INFORMATION:  
   >   
   >  Instance of the WMI class is not found. (WinMgmt)  
   >   
   >  This error can occur because the BizTalk databases are not available while they are being failed over. To workaround this issue, wait until after the clustered instance of SQL Server is online before attempting to connect to it with the BizTalk Server Administration console.  
  
## See Also  
 [Managing Groups](../core/managing-groups.md)   
 [BizTalk Groups](../core/biztalk-groups.md)