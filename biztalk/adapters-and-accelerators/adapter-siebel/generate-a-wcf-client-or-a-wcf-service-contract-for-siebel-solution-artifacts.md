---
title: "Generate a WCF client or a WCF service contract for Siebel solution artifacts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "how to, generate a client class by using svcutil.exe"
  - "creating a proxy"
  - "how to, create a proxy"
  - "WCF service model, creating a proxy"
  - "how to, generate a client class by using the Add Adapter Service Reference Plug-in"
  - "how to, generate a client class"
ms.assetid: 52c32c86-6403-4bb4-9d43-1319d19a6b49
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generate a WCF client or a WCF service contract for Siebel solution artifacts
You can use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class targeted at selected operations on Siebel artifacts. You can also use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate the WCF client class; however, the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] exposes the functionality of the ServiceModel Metadata Utility Tool through a standard Microsoft Windows interface. It also provides browse and search capabilities that are not available with the svcutil.exe tool, and generates a configuration file based on the binding properties that you select when you connect to the Siebel system.  
  
## Generating a WCF Client Class by Using the Add Adapter Service Reference Plug-in  
 Perform the following steps to generate a WCF client class by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### To generate a WCF client class  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click your project, and then click **Add Adapter Service Reference**.  
  
2. After the **Add Adapter Service Reference** dialog box opens, follow the steps in [Retrieving Metadata for Siebel Operations in Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md) to connect to the Siebel system and browse and search for operations. To create a WCF client class for the operations that you select, be sure that **Client (Outbound operations)** is selected from the **Select contract type** drop-down list (this is the default).  
  
3. After you select all of the operations that you want to target, click **OK** to generate the WCF client class.  
  
   The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] adds two files to your project:  
  
- The WCF client code file. This file contains the generated WCF client class and helper code for the operations that you selected. The first time you run the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] it will generate this file with the default name **SiebelBindingClient.cs** . If you run it again, the next file it generates will be called **SiebelBindingClient1.cs**.  The number suffix will increase by 1 for every new file you generate.  You can also change the default prefix **SiebelBinding** by entering a different prefix in the **Filename prefix** field of the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] before selecting **OK** to generate the file.  
  
- **App.config**. This file contains a binding configuration and client endpoint configurations that are based on the selections you made when you configured the connection for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. For more information about the contents of the app.config file, see [Configure a WCF Client for a Siebel System](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).  
  
  > [!IMPORTANT]
  >  While using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], if you do not specify a value for a binding property of type string and whose default value is null then that binding property will not be available in the app.config file. You must manually add the binding property and its value in the app.config file, if required.  
  
## Generating a WCF Client Class by Using svcutil.exe  
 You can use svcutil.exe to generate a WCF client class for your application. You must configure svcutil.exe to use it with the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]. For more information about configuring and using svcutil.exe with the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md).  
  
 Svcutil.exe generates the WCF client class in an output file with a default file name of output.cs. You must manually include this file in your [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] project.  
  
## See Also  
 [Develop Siebel Applications using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)