---
title: "How to Create a Linked Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servers, linking for backups"
  - "backing up, linking servers"
ms.assetid: 7d4aba3d-77c0-4cdf-8547-71e821ce34a1
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Linked Server
When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed in a distributed topology, the databases that belong to a BizTalk Group exist on multiple [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. You must configure a linked server connection to each of the remote servers before you can back up the entire BizTalk environment from the BizTalk Management server. A linked server is an OLE DB data source that is used in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] distributed queries.  
  
 As a part of the backup and restore process, the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job automatically creates linked servers. If necessary, however, you can manually create linked servers using this procedure.  
  
 Linked servers can also be created using the *sp_addlinkedserver* stored procedure. There are security considerations associated with this operation. When a linked server is created using sp_addlinkedserver, all local logins will be mapped to the new linked server by default. To control access to the linked server, the *sp_droplinkedsvrlogin* procedure should be used to drop the global login mapping, followed by *sp_addlinkedsvrlogin* to map the desired login account(s) to the new linked server. When using sp_addlinkedsvrlogin, it is recommended that you set the @useself parameter = TRUE. This avoids the need to embed a user name and password into your SQL script.  

> [!TIP]
> These steps may change over time. We recommend referring to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation at [Create Linked Servers](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine).
  
## Prerequisites  
  
- Sign in with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] **sysadmin** fixed server role  
  
- Create a local [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] login. In the following steps, this account is mapped to a login on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] you will link to. 
  
## Create a linked server
  
1. Open **SQL Server Management Studio**, enter the name of your local [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and then select **Connect**.  
  
2. Expand **Server Objects**, right-click **Linked Servers**, and then select **New Linked Server**.  

   To see **Server Objects**, connect to a local on-premises [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Then, **Server Objects** should be displayed.
  
3. In the **Linked server** text box, enter the full network name of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] you want to link to.  
  
   > [!NOTE]
   >  This procedure often refers to the server you are linking to as the remote server. This is for convenience only, to indicate the relationship of the linked (“remote”) server to the local server.  
  
4. Under **Server type**, select **SQL Server**.  
  
5. In the left pane, select **Security**. 

   In this step, you map the local account you created to the remote server login. Your options: 
    
   | | | 
   |---|---|
   | **Be made using the login’s current security context** | In domain environments, users typically connect with their domain logins. This option may be best since the security context of the signed-in domain account is mapped to the local account you created.|
   | **Be made using this security context** | When users connect to the local SQL Server using a SQL Server login, then this option may be best. Then enter the login and password for the account on the linked server. |


6. Select **Add**, and enter the following: 

   1. Under **Local Login**, select the local account you created. 
   2. Check **Impersonate** if the local login also exists on the remote server. 
   3. Alternatively, if the local login will be mapped to a remote [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] login you, enter the **Remote User** name and **Remote Password** for the remote server login.  
  
      > [!NOTE]
      >  To use impersonation, your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] configuration and login accounts must meet the requirements for delegation. See [Configuring Linked Servers for Delegation](https://msdn.microsoft.com/library/ms189580.aspx) for more details.  

7. In the left pane, choose **Server Options**. Set the **RPC** and **RPC Out** parameters to **True**, and then select **OK**. 
 
> [!TIP]
> For more details and recommendations when creating linked servers, includig using the `sp_addlinkedserver` stored procedcure, see [Create Linked Servers](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine).

  
## See Also  
 [Advanced Information About Backup and Restore](../core/advanced-information-about-backup-and-restore1.md)