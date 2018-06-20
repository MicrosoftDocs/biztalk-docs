---
title: "Connect to Oracle Database using the adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connection string"
  - "uniform resource identifier"
  - "Oracle database, connecting to"
  - "URI"
  - "connection URI"
ms.assetid: 5d5598e5-aba0-4c73-8e97-9156475b93c4
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to Oracle Database using the adapter
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] uses ODP.NET 11.1.0.7 to connect to the Oracle database. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] requires adapter clients to provide a connection string, called the connection Uniform Resource Identifier (URI), to connect to the Oracle database. Internally, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] maps the URI to a database connection string to connect to the Oracle database. With a connection URI, adapter clients can specify connection parameters to connect to an external system.  
  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] enables adapter clients to connect to the Oracle database in the following two ways:  
  
- **Using tnsnames.ora**: The connection URI provided by the adapter client contains only the net service name specified in the tnsnames.ora file. The adapter extracts the connection parameters such as server name, service name, and port number from the net service name entry in the tnsnames.ora file. To use this approach, the computer running the Oracle client must be configured to include the net service name for the Oracle database in the tnsnames.ora file.  
  
  > [!IMPORTANT]
  >  Due to an Oracle Client limitation, the **DataSourceName** parameter (net service name) in the [Configure the connection URI for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-the-connection-uri-for-the-oracle-database-adapter.md) cannot contain more than 39 characters if you are performing operations in a transaction. Therefore, make sure that the value specified for the **DataSourceName** parameter is less than or equal to 39 characters if you will be performing operations in a transaction.  
  
- **Without using tnsnames.ora**: The connection URI provided by the adapter clients contains the connection parameters such as server name, service name, and port number. In this case, the net service name in the tnsnames.ora file, or the actual tnsnames.ora file itself, does not need to be present on the client computer. This is helpful when you have a large number of users connecting to the Oracle database in your organization, and adding/updating servers does not lead to manually adding/updating the connection details in the tnsnames.ora file on every client computer.  
  
  > [!IMPORTANT]
  >  This mode of connectivity is not supported if you are performing operations in a transaction. This is due to a limitation of Oracle Client.  
  
  For more information about connecting to the Oracle database, see [Create a connection to the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md).  
  
  Make sure you comply with the security guidelines when establishing a connection with the Oracle database. For more information about security guidelines, see [Secure your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md).  
  
## Windows Authentication  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports Windows Authentication while connecting to the Oracle database. With Windows Authentication, the adapter clients can determine a user’s identity based on Windows logon credentials, and can leverage the built-in security of the Windows environment. For information about connecting to the Oracle database by using Windows Authentication, see [Connect to the Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md).  
  
## See Also  
 [Overview of BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)