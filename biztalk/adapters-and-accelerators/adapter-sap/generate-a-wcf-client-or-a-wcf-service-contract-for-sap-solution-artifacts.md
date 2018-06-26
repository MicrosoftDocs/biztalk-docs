---
title: "Generate a WCF client or a WCF service contract for SAP solution artifacts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff01e2b0-6480-427a-bc6d-6169e7d6e256
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generate a WCF client or a WCF service contract for SAP solution artifacts
You can use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or a WCF service contract (interface) targeted at selected operations on SAP artifacts. You can also use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate the WCF client class or WCF service contract; however, the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] exposes the functionality of the ServiceModel Metadata Utility Tool through a standard Microsoft Windows interface. It also provides browse and search capabilities that are not available with the svcutil.exe tool, and generates a configuration file based on the binding properties that you select when you connect to the SAP system.  
  
## Generating a Client Class by Using the Add Adapter Service Reference Plug-in  
 Perform the following steps to generate a WCF client class by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### To generate a WCF client class  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click your project, and then click **Add Adapter Service Reference**.  
  
2. After the **Add Adapter Service Reference** dialog box opens, follow the steps in [Get Metadata for SAP Operations in Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md) to connect to the SAP system and browse and search for operations. To create a WCF client class for the operations that you select, be sure that **Client (Outbound operations)** is selected from the **Select contract type** drop-down list (this is the default).  
  
3. After you select all of the operations that you want to target, click **OK** to generate the WCF client class.  
  
   The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] adds two files to your project:  
  
- **SAPBindingClient.cs**. This file contains the generated WCF client class and helper code for the operations that you selected.  
  
- **App.config**. This file contains a binding configuration and client endpoint configurations. The settings are based on the selections you made when you configured the binding and connection for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
  > [!IMPORTANT]
  >  While using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], if you do not specify a value for a binding property of type string and whose default value is null then that binding property will not be available in the app.config file. You must manually add the binding property and its value in the app.config file, if required.  
  
## Generating a WCF Service Contract by Using the Add Adapter Service Reference Plug-in  
 When you use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to receive IDOCs, RFCs, and tRFCs from the SAP system, your code acts as a service to the adapter. That is, the adapter receives the appropriate artifact from the SAP system and then invokes an (inbound) operation on your code to deliver the artifact to your application.  
  
 You must, therefore, implement a WCF service that can receive this inbound operation from the adapter. To do this, you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a .NET interface that represents the service contract that is surfaced by the adapter for the operation. This .NET interface is also called a WCF service contract. The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a class that contains a stubbed implementation of the WCF service. You then implement this interface to create the WCF service that you can use to receive the operation.  
  
 Perform the following steps to generate a WCF service contract by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### To generate a WCF service contract  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click your project, and then click **Add Adapter Service Reference**.  
  
2. After the **Add Adapter Service Reference** dialog box opens, follow the steps in [Get Metadata for SAP Operations in Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md) to connect to the SAP system and browse and search for operations. To create a WCF service contract for the operations that you select, be sure that **Service (Inbound operations)** is selected from the **Select contract type** drop-down list.  
  
3. After you select all of the operations that you want to target, click **OK** to generate the WCF service contract.  
  
   The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] adds three files to your project:  
  
- **SAPBindingInterface.cs**. This file contains the generated WCF service contract (interface) and helper code for the operations that you selected.  
  
- **SAPBindingService.cs**. This file contains a stubbed WCF service class that implements the interface defined in SAPBindingInterface.cs. You can implement the business logic that processes the RFC, tRFC or IDOC directly in the methods of this class.  
  
- **App.config**. This file contains a binding configuration, endpoint behaviors, and service endpoint configuration that are based on the selections you made when you configured the binding and connection for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
  > [!IMPORTANT]
  >  While using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], if you do not specify a value for a binding property of type string and whose default value is null then that binding property will not be available in the app.config file. You must manually add the binding property and its value in the app.config file, if required.  
  
> [!NOTE]
>  You do not have to specify RFC Server parameters when you configure the connection URI for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate the WCF service contract. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] retrieves metadata from the SAP system through a client connection.  
  
## Generate a WCF Client Class or a WCF Service Contract by Using svcutil.exe  
 You can use svcutil.exe to generate a WCF client class or a WCF service contract for your application. You must configure svcutil.exe to use it with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. For more information about configuring and using svcutil.exe with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md).  
  
 Svcutil.exe generates the WCF client class or WCF service contract in an output file. The default file name is output.cs. You must manually include this file in your [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] project.  
  
## See Also  
[Develop SAP applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)