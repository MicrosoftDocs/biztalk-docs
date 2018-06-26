---
title: "Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7ffd857-a177-423a-ae83-685d11b7aec6
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts
You can use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or a WCF service contract (interface) targeted at selected operations on Oracle E-Business Suite artifacts. You can also use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate the WCF client class or WCF service contract; however, the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] exposes the functionality of the ServiceModel Metadata Utility Tool through a standard Microsoft Windows interface. It also provides browse and search capabilities that are not available with the svcutil.exe tool, and it generates a configuration file based on the binding properties that you select when you connect to the Oracle E-Business Suite.  
  
## Generating a Client Class by Using the Add Adapter Service Reference Plug-in  
 Perform the following steps to generate a WCF client class by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### To generate a WCF client class  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click your project, and then click **Add Adapter Service Reference**.  
  
2. After the **Add Adapter Service Reference** dialog box opens, follow the steps in [Retrieving Metadata for Oracle E-Business Suite Operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md) to connect to the Oracle E-Business Suite and browse and search for operations. To create a WCF client class for the operations that you select, be sure that **Client (Outbound operations)** is selected from the **Select contract type** drop-down list (this is the default).  
  
3. After you select all of the operations that you want to target, click **OK** to generate the WCF client class.  
  
   The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] adds two files to your project:  
  
- **OracleEBSBindingClient.cs**. This file contains the generated WCF client class and helper code for the operations that you selected.  
  
- **app.config**. This file contains a binding configuration and client endpoint configurations. These configurations are based on the selections you made when you configured the binding and connection for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
  > [!IMPORTANT]
  >  While using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], if you do not specify a value for a binding property of type string and whose default value is null then that binding property will not be available in the app.config file. You must manually add the binding property and its value in the app.config file, if required.  
  
## Generating a WCF Service Contract by Using the Add Adapter Service Reference Plug-in  
 The adapter exposes inbound operations to enable Oracle E-Business Suite to send messages to an adapter client. For such operations you must generate a WCF service contract. This section provides information on how to generate a service contract for inbound operations exposed by the adapter.  
  
 Perform the following steps to generate a WCF service contract by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### To generate a WCF service contract for inbound operations  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click your project, and then click **Add Adapter Service Reference**.  
  
2. After the **Add Adapter Service Reference** dialog box opens, follow the steps in [Retrieving Metadata for Oracle E-Business Suite Operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md) to connect to the Oracle E-Business Suite. There are several binding properties and a URI property that you may want to set when you connect to the Oracle E-Business Suite.  
  
3. After you have connected to the Oracle E-Business Suite, select **Service (Inbound operations)** from the **Select contract type** drop-down list.  
  
4. In the **Select a category** box, browse to the inbound operation for which you want to generate the service contract. For example, for **Notification** operation, click the root node (**/**), select **Notification** from the **Available categories and operations** box, and then click **Add**. For instructions on how to browse for inbound operations, see [Browse, Search, and Retrieving Metadata for Oracle E-Business Suite Operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
5. To generate the WCF service contract for the operation, click **OK**.  
  
   The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] adds three files to your project:  
  
- **OracleEBSBindingInterface.cs**. This file contains the generated WCF service contract (interface) and helper code for the inbound operation.  
  
- **OracleEBSBindingService.cs**. This file contains a class that implements the interface defined in OracleDBBindingInterface.cs. You can implement the business logic that processes the records returned by the inbound operation.  
  
- **app.config**. This file contains a binding configuration, endpoint behaviors, and service endpoint configuration that are based on the selections you made when you configured the binding and connection for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
  > [!IMPORTANT]
  >  While using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], if you do not specify a value for a binding property of type string and whose default value is null then that binding property will not be available in the app.config file. You must manually add the binding property and its value in the app.config file, if required.  
  
## Using svcutil.exe to Generate a WCF Client Class or a WCF Service Contract  
 You can use svcutil.exe to generate a WCF client class or a WCF service interface for your application. You must configure svcutil.exe to use it with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
 Svcutil.exe generates the WCF client class or WCF service contract in an output file. The default file name is output.cs. You must manually include this file in your [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] project. For more information about svcutil.exe, see [http://go.microsoft.com/fwlink/?LinkId=139432](http://go.microsoft.com/fwlink/?LinkId=139432).