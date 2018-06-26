---
title: "Connect to the SAP System in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SAP system, connecting to"
  - "Add Adapter Service Reference Visual Studio Plug-in"
  - "Consume Adapter Service BizTalk Project Add-in"
ms.assetid: 5fc356b1-05e8-4235-bb04-5ef6192c5291
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to the SAP System in Visual Studio
This section provides information about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
- The **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** is available in BizTalk Server projects. You use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with BizTalk Server, see [Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).  
  
- The **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** is available in BizTalk Server projects. You use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with BizTalk Server, see [Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).  
  
  > [!NOTE]
  >  Because the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is exposed both as a WCF-Custom binding and as BizTalk adapter, you can use either the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] from a BizTalk project to connect to an SAP system.  
  
- The **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** is available in non-BizTalk programming projects. You use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client class or a WCF service callback interface when you develop solutions using the WCF service model. For more information about developing solutions with the WCF service model, see [Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).  
  
  To use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] you must first connect to the SAP system. All three user interface present a dialog box through which you configure a connection by setting the following:  
  
- **Connection parameters**. These are the parameters that are used to build the connection URI such as application server host or message server host, and client ID.  
  
- **User name password credentials for the SAP system**. These are used to authenticate you on the SAP system when the connection is established. You must specify a user name and password.  
  
- **Binding properties**. Binding properties are optional and whether you specify them depends primarily on whether you target operations that require specific binding properties to be set. For example, for a ReceiveIdoc operation you must set the **ReceiveIdocFormat** binding property to String. For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
  At a minimum, when you configure the connection to the SAP system, you only have to specify binding properties and connection parameters that are needed to establish the connection and that affect the metadata returned by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for the operations you want to target. However, you might also want to specify values for any additional binding properties and connection parameters that will be used at run time. This is because:  
  
- The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] creates a BizTalk port binding file from the binding properties and connection parameters that you specify when you configure the connection and adds this file to your project.  
  
- The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] creates an app.config file from the binding properties and connection properties that you specify when you configure the connection and adds this file in your project directory.  
  

  
## See Also  
 [Get Metadata for SAP Operations in Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)