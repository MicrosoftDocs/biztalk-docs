---
title: "Connect to SQL Server using Windows Authentication with the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45c54b2a-e056-496f-9f10-f19b6a3ca1a6
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to SQL Server using Windows Authentication with the SQL adapter
The [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] enables adapter clients to use Windows Authentication to establish a connection with SQL Server. To use Windows Authentication, adapter clients must enter an empty user name and password. 

To connect to SQL Server using Windows Authentication within Visual Studio, see [Connect to SQL Server in Visual Studio using the Consume Adapter Service Add-in](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md).  
  
 To enable adapter clients to use Windows Authentication to connect to SQL Server, enable Windows Authentication for the user on the computer running SQL Server.  

> [!TIP]
> If SQL Server Management Studio is not installed on your SQL Server, you can [Download SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms), and install it. 
 
## Add the user in SQL Server  
  
1.  Open SQL Server Management Studio. In **Connect to Server**, select **Database Engine**, enter your SQL **Server name**, and enter administrator credentials to connect to the server.  

    Select **Connect**.
  
2.  In **Object Explorer**, expand the SQL Server, expand **Security**, right-click **Logins**, and then select **New Login**.  
  
3.  For the **Login name**, enter the Windows user name in the `domain\username` format.  

    > [!NOTE]
    >* When using this adapter with BizTalk, then the login name you enter, is the identity of the host instance account.  
    >
    >* When using this adapter in .NET code, then the login name you enter, is the identity for that process.
  
4.  Select **User Mapping** (left pane). Select a database to associate with the user. A typical BizTalk user should be associated with the following databases: 

* BizTalkDTADb
* BizTalkMgmtDb
* BizTalkMsgBoxDb
* BTAHL7
* SSODB

5. In the **Database role membership for** box, select **db_owner** for all the BizTalk databases.  

    > [!NOTE]
    > [Server and Database Roles in SQL Server](https://msdn.microsoft.com/library/bb669065.aspx) provides good info on the roles. 
  
6. Select **OK** to save your changes.
  
   After you have added the user, the user can connect and authenticate to SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], logging in with a blank username and password.  



## See Also  
 [Create a connection to SQL Server](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)