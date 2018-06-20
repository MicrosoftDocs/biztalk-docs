---
title: "Generate a WCF client or a WCF service contract for Oracle Database solution artifacts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF service model programming, creating a proxy"
  - "how to, create a proxy"
  - "creating a proxy"
  - "proxy programming, creating a proxy"
ms.assetid: 3e832ae9-e253-4476-9f25-8cf0de12f469
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generate a WCF client or a WCF service contract for Oracle Database solution artifacts
You can use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or a WCF service contract (interface) targeted at selected operations on Oracle database artifacts. You can also use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate the WCF client class or WCF service contract; however, the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] exposes the functionality of the ServiceModel Metadata Utility Tool through a standard Microsoft Windows interface. It also provides browse and search capabilities that are not available with the svcutil.exe tool, and it generates a configuration file based on the binding properties that you select when you connect to the Oracle database.  
  
## Generating a Client Class by Using the Add Adapter Service Reference Plug-in  
 Perform the following steps to generate a WCF client class by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### To generate a WCF client class  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click your project, and then click **Add Adapter Service Reference**.  
  
2. After the **Add Adapter Service Reference** dialog box opens, follow the steps in [Retrieve metadata for Oracle operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) to connect to the Oracle database and browse and search for operations. To create a WCF client class for the operations that you select, be sure that **Client (Outbound operations)** is selected from the **Select contract type** drop-down list (this is the default).  
  
3. After you select all of the operations that you want to target, click **OK** to generate the WCF client class.  
  
   The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] adds two files to your project:  
  
- **OracleDBBindingClient.cs**. This file contains the generated WCF client class and helper code for the operations that you selected.  
  
- **App.config**. This file contains a binding configuration and client endpoint configurations. These configurations are based on the selections you made when you configured the binding and connection for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
  > [!IMPORTANT]
  >  While using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], if you do not specify a value for a binding property of type string and whose default value is null then that binding property will not be available in the app.config file. You must manually add the binding property and its value in the app.config file, if required.  
  
## Generating a WCF Service Contract by Using the Add Adapter Service Reference Plug-in  
 The adapter exposes inbound operations to enable Oracle database to send messages to an adapter client. For such operations you must generate a WCF service contract. For example, the adapter exposes an inbound POLLINGSTMT operation to poll the Oracle database. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes the query specified by the **PollingStatement** binding property and sends the result set to the consuming application in a POLLINGSTMT message. In this scenario, the consuming application acts as a service and the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] acts as the client. You must, therefore, implement a WCF service that can receive the POLLINGSTMT operation from the adapter. To do this, you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a .NET interface that represents the service contract that is surfaced by the adapter for the POLLINGSTMT operation. This .NET interface is also called a WCF service contract. You then implement this interface to create the WCF service that you can use to receive the POLLINGSTMT operation.  
  
 This section provides information on how to generate a WCF service contract using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] for inbound operations exposed by the adapter.  
  
#### To generate a WCF service contract for inbound operations  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click your project, and then click **Add Adapter Service Reference**.  
  
2. After the **Add Adapter Service Reference** dialog box opens, follow the steps in [Retrieve metadata for Oracle operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) to connect to the Oracle database. There are several binding properties and a URI property that you may want to set when you connect to the Oracle database for inbound operations. For example, for the inbound polling operation (**POLLINGSTMT**), you must specify the **PollingStatement** binding property when you configure the connection to the Oracle database. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses the SQL SELECT statement specified in this property to generate the class that represents the result set returned by the POLLINGSTMT operation.  
  
3. After you have connected to the Oracle database, select **Service (Inbound operations)** from the **Select contract type** drop-down list.  
  
4. In the **Select a category** box, click the root node (**/**), and browse to the operation for which you want to generate the service contract. For example, for the polling operation, select **POLLINGSTMT** from the **Available categories and operations** box, and then click **Add**.  
  
5. To generate the WCF service contract for the POLLINGSTMT operation, click **OK**.  
  
   The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] adds three files to your project:  
  
- **OracleDBBindingInterface.cs**. This file contains the generated WCF service contract (interface) and helper code for the POLLINGSTMT operation.  
  
- **OracleDBBindingService.cs**. This file contains a class that implements the interface defined in OracleDBBindingInterface.cs. You can implement the business logic that processes the records returned by the polling query in the POLLINGSTMT method in this class.  
  
- **App.config**. This file contains a binding configuration, endpoint behaviors, and service endpoint configuration that are based on the selections you made when you configured the binding and connection for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
  > [!IMPORTANT]
  >  While using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], if you do not specify a value for a binding property of type string and whose default value is null then that binding property will not be available in the app.config file. You must manually add the binding property and its value in the app.config file, if required.  
  
## Using svcutil.exe to Generate a WCF Client Class or a WCF Service Contract  
 You can use svcutil.exe to generate a WCF client class or a WCF service interface for your application. You must configure svcutil.exe to use it with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. For more information about configuring and using svcutil.exe with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md).  
  
 Svcutil.exe generates the WCF client class or WCF service contract in an output file. The default file name is output.cs. You must manually include this file in your [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] project.  
  
## See Also  
 [Develop Oracle Database Applications by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)   
 [Performing Basic Insert, Update, Delete, and Select Operations in SQL Using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/insert-update-delete-or-select-operations-in-sql-using-the-wcf-service-model.md)