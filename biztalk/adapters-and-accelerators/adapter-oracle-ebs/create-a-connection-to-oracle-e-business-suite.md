---
title: "Create a connection to Oracle E-Business Suite | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eeeab604-155e-4806-b77a-45319a3f8cc0
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create a connection to Oracle E-Business Suite
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding. As such, it enables communication to Oracle E-Business Suite through a WCF endpoint address. In WCF the endpoint address identifies the network location of a service and is typically expressed as a Uniform Resource Identifier (URI). The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses to establish a connection to Oracle E-Business Suite. You must specify a connection URI when you:  
  
- Create a channel factory or a channel listener using the WCF channel model or when you create a WCF client or service host using the WCF service model.  
  
- Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
- Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or WCF service interface for a WCF service model solution.  
  
- Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] for a BizTalk Server solution.  
  
- Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class or WCF service interface for a WCF service model solution.  

## Ways to connect to Oracle  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports two ways of establishing a connection to the underlying Oracle database:  
  
-   **Using tnsnames.ora**. In this approach, the connection URI provided by the adapter client contains only the net service name entered in the tnsnames.ora file. The adapter extracts the connection parameters, such as server name, service name, port number, and so on, from the net service name entry in the file. To use this approach, the computer running the Oracle client must be configured to include the net service name for the Oracle database in the tnsnames.ora file.  
  
    > [!IMPORTANT]
    >  Due to an Oracle Client limitation, the **DataSourceName** parameter (net service name) in the [Create the Oracle E-Business Suite connection URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md) cannot contain more than 39 characters if you are performing operations in a transaction. Therefore, if you are performing operations in a transaction, make sure that the **DataSourceName** parameter value is less than or equal to 39 characters.  
  
-   **Without using tnsnames.ora**. In this approach, the adapter clients enter the connection parameters directly in the connection URI. This does not require the net service name to be present in the tnsnames.ora file on the client computer. This approach does not even require the tnsnames.ora file to be present on the client computer.  
  
    > [!IMPORTANT]
    >  This mode of connectivity is not supported if you are performing operations in a transaction. This is due to a limitation of Oracle Client.  

## In this section    
 The following topics describe how to establish a connection between the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] and Oracle E-Business Suite:  
  
-   [Configure the Oracle client for the E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md): Information about using tnsnames.ora to cconfiguring the Oracle client (required only if using the tnsnames.ora to establish the connection)  
  
-   [Create the Oracle E-Business Suite connection URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md): Information about the connection properties and the structure of the Oracle E-Business Suite connection URI
  
-   [Connect to Oracle E-Business Suite using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md): Information about connecting to Oracle using Windows Authentication
  