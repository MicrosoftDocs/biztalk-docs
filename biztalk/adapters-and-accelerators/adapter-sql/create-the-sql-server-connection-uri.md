---
title: "Create the SQL Server connection URI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 688e2215-a4d8-4f55-a37c-7d91c3de080f
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create the SQL Server connection URI
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] connection URI contains properties that the adapter uses to establish a connection to the SQL Server database. This topic provides information about the SQL Server connection URI, and provides links to other topics that explain how to specify a URI in different programming scenarios.  
  
##  <a name="FailoverPartner"></a> The Connection URI for the SQL Adapter  
 A typical endpoint address URI in WCF is represented as: `scheme://hostinfoparams?query_string`, where:  
  
- scheme is the scheme name.  
  
- hostinfoparams is information required to establish the connection to the host; for example, a server name.  
  
- query_string is an optional name-value collection of parameters delimited by a question mark (?).  
  
  The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] connection URI adheres to this basic format and is implemented as follows:  
  
```  
  
mssql://[Server_Name[:Portno]]/[Database_Instance_Name]/[Database_Name]?FailoverPartner=[Partner_Server_Name]&InboundId=[Inbound_ID]  
```  
  
 where, `mssql` is the scheme for the SQL Server connection URI.  
  
 The following table explains the properties contained in the connection URI.  
  
|Connection URI Property|Category|Description|  
|-----------------------------|--------------|-----------------|  
|[SERVER_NAME]|hostinfoparams|Name of the server on which SQL Server is installed. If you do not specify a value, the adapter assumes the server name as “localhost” and establishes a connection with the SQL Server database on the local server.|  
|[PORTNO]|hostinfoparams|The port number where the connection is established. If you do not specify a value, the adapter connects through the default port.|  
|[DATABASE_INSTANCE_NAME]|hostinfoparams|Name of the SQL Server instance to connect to. If you do not specify a value, the adapter connects to the default database instance.|  
|[DATABASE_NAME]|hostinfoparams|Name of the database to connect to. If you do not specify a value, the adapter connects to the default database.|  
|[PARTNER_SERVER_NAME]|query_string|Name of the failover SQL Server database to connect to if the primary SQL Server database is not available. For more information about high availability with respect to SQL Server, see [Database Mirroring in SQL Server](https://msdn.microsoft.com/library/5h52hef8.aspx).|  
|[INBOUND_ID]|query_string|An identifier that you add to the connection URI to make it unique. You must provide this connection parameter if you want to generate metadata for the **TypedPolling** inbound operation. Also, in a BizTalk application, if you have multiple receive locations polling the same database, the inbound ID makes the connection URI unique, thereby enabling adapter clients to receive polling messages from the same database on different receive locations. For more information, see [Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md).|  
  
> [!NOTE]
>  For more information about these connection string properties, see [SqlConnection.ConnectionString Property](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx).
  
## SQL Server Credentials and the Connection URI  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support specifying credentials in the connection URI. For more information about specifying credentials in your applications that use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Secure your SQL applications](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md).  
  
## Using Special Characters in the Connection URI  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support specifying a connection URI that has special characters for any of the parameter values. If the connection parameter values contain special characters, make sure you do one of the following:  
  
- If you are specifying the URI in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] using [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters. If you specify the URI directly in the **Configure a URI** field and the connection parameters contain special characters, you must specify the connection parameters using proper escape characters.  
  
   For example, if the connection URI has a parameter with name `sql server`, you must specify it as `sql%20server`.  
  
- If you are specifying the URI while creating a send or receive port in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, and the connection parameters contain special characters, you must specify the connection parameters using proper escape characters.  
  
## Using the Connection URI to Connect to the SQL Server Database  
 The following is a sample connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
```  
mssql://sql_server/sql_server_instance//  
```  
  
 In the preceding example, “sql_server” is the name of the computer on which SQL Server is installed whereas “sql_server_instance” is the name of the database instance to connect to. Because no database name is specified, the adapter will connect to the default database.  
  
 The following is an example of a connection URI where the SQL Server database is installed on the same computer as the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. In this example, the adapter connects to the database “my_database” for the “sql_server_instance” database instance on the local computer.  
  
```  
mssql://localhost/sql_server_instance/my_database/  
```  
  
 In this example, the adapter connects to the default database for the default instance running on the local computer.  
  
```  
mssql://localhost///  
```  
  
 For information about how to specify a connection to the SQL Server database when you:  
  
- Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], see [Connect to SQL Server in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md).  
  
- Configure a send port or receive port (location) in a BizTalk Server solution, see [Manually configure a physical port binding to the SQL adapter](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).
  
- Use the WCF channel model in a programming solution, see [Create a channel using the SQL adapter](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md).  
  
- Use the WCF service model in a programming solution, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).  
  
## See Also  
[Develop your SQL applications](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)