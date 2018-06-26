---
title: "How to Add a New MessageBox Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adding, MessageBox database"
  - "MessageBox database, adding"
  - "managing [MessageBox database], adding"
ms.assetid: 98d850dc-fe3e-43dd-8b5d-9b8c23c006ae
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a New MessageBox Database
You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console to add a new MessageBox database to your BizTalk Server deployment. MessageBox databases are the basis for load-balancing work items across servers that do cooperative processing. To increase the number of messages that your system can process, you may need to add additional MessageBox databases.  
  
 You cannot create a new MessageBox database and have enlisted orchestrations, send ports, or send port groups at the same time. Enlisted orchestrations, send ports, or send port groups access data that BizTalk Server must copy to the new MessageBox database. While this data is being accessed, BizTalk Server cannot copy it into the new MessageBox database.  
  
 You can designate both local and remote databases as MessageBox databases. For information about BizTalk Server databases, see [Databases in BizTalk Server](../core/databases-in-biztalk-server.md).  
  
> [!IMPORTANT]
>  SQL Server Agent must be running on all of the SQL servers to which you want to add a new MessageBox database.  
  
## Prerequisites  
 Administrators who manage MessageBox databases must have the required user rights. You must have the following user rights to manage MessageBox databases and disable new message publication:  
  
-   You must be logged on as a member of the BizTalk Server Administrators group.  
  
-   You must be a SQL Server Administrator on the computer where the database exists.  
  
### To add a new MessageBox database  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then click **Platform Settings**.  
  
3. Right-click **Message Boxes**, click **New**, and then click **Message Box**.  
  
4. In the **Message Box Properties** dialog box, do the following, and then click **OK**:  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**SQL Server**|Displays the name of the SQL server that hosts the MessageBox database.|  
   |**Database**|Displays the name of the MessageBox database.|  
   |**Master subscription message box**|Indicates whether the selected MessageBox database is the master. If the current MessageBox database is the master, this check box is selected and unavailable. The first MessageBox database created when you run the Configuration Wizard is the master by default.|  
   |**Disable new message publication**|Select this check box to specify that you do not want this MessageBox database to receive activation messages.|  
  
## See Also  
 [Managing MessageBox Databases](../core/managing-messagebox-databases.md)   
 [How to Disable New Message Publication](../core/how-to-disable-new-message-publication.md)   
 [How to Delete a MessageBox Database](../core/how-to-delete-a-messagebox-database.md)   
 [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md)   
 [The MessageBox Database](../core/the-messagebox-database.md)