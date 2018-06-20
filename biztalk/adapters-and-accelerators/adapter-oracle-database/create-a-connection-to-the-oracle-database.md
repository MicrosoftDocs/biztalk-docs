---
title: "Create a connection to the Oracle Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapter, connecting to the Oracle Database"
ms.assetid: 95f7905a-abad-4841-85c4-62cf0cc1e044
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create a connection to the Oracle Database
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding. As such, it enables communication to an Oracle database through a WCF endpoint address. In WCF, the endpoint address is typically expressed as a Uniform Resource Identifier (URI), which identifies the network location of the service. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses to establish a connection to the Oracle database.  
  
 You must specify a connection URI when you:  
  
- Create a channel factory or a channel listener using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model or when you create a WCF client or service host using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model.  
  
- Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
- Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or WCF service interface for a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model solution.  
  
- Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] for a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
- Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class or WCF service interface for a WCF service model solution.  
  
  The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports two ways of establishing a connection to the Oracle database:  
  
- **Using tnsnames.ora**. In this approach, the connection URI provided by the adapter client contains only the net service name specified in the tnsnames.ora file. The adapter extracts the connection parameters such as server name, service name, port no, etc. from the net service name entry in the file. To use this approach, the computer running the Oracle client must be configured to include the net service name for the Oracle database in the tnsnames.ora file.  
  
  > [!IMPORTANT]
  >  Due to an Oracle Client limitation, the **DataSourceName** parameter (net service name) in the [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md) cannot contain more than 39 characters if you are performing operations in a transaction. Therefore, make sure that the value specified for the **DataSourceName** parameter is less than or equal to 39 characters if you will be performing operations in a transaction.  
  
- **Without using tnsnames.ora**. In this approach, the adapter clients specify the connection parameters directly in the connection URI. This does not require the net service name to be present in the tnsnames.ora file on the client computer. This approach does not even require the tnsname.ora file to be present on the client computer.  
  
  > [!IMPORTANT]
  >  This mode of connectivity is not supported if you are performing operations in a transaction. This is due to a limitation of Oracle Client.  
  
  The topics in this section describe how to establish a connection between the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] and the Oracle database by providing you with:  
  
- Information about configuring the Oracle client.  
  
- Information about the connection properties and the structure of the Oracle connection URI.  
  
- Links to topics that show how to establish a connection by using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
- Information about connecting to the Oracle database using Windows Authentication.  
  
## In This Section  
  
-   [Configure the Oracle Client for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)  
  
-   [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)  
  
-   [Connect to the Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)  
  
## See Also  
[Develop your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)