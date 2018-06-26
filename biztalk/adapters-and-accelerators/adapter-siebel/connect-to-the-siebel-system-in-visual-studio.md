---
title: "Connect to the Siebel System in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Add Adapter Service Reference Plug-in"
  - "Consume Adapter Service Add-in"
  - "how to, connect to the Siebel System in Visual Studio"
ms.assetid: 4a94bce9-fda9-4e00-b26c-08672a80e3be
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to the Siebel System in Visual Studio
This section provides instructions about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
- The **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** is available in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects and is installed as part of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. You use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Develop BizTalk applications using the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md).  
  
- The **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** is available in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects and is installed as part of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] installation. You use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Develop BizTalk applications using the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md).  
  
  > [!NOTE]
  >  Because the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is exposed both as a WCF-Custom binding and as BizTalk adapter, you can use either the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] from a BizTalk project to connect to a Siebel system.  
  
- The **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** is available in non-BizTalk programming projects. You use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client class or a WCF service callback interface when you develop solutions using the WCF service model. For more information about developing solutions with the WCF service model, see [Develop Siebel applications using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).  
  
  To use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], you must first connect to the Siebel system. All three methods present a dialog box through which you configure a connection by setting the following:  
  
- **Connection parameters**. These are the parameters that are used to build the connection URI such as the name of the Siebel Enterprise Server.  
  
- **User name password credentials for the Siebel system**. These are used to authenticate you on the Siebel system when the connection is established. You must specify a user name and password.  
  
- **Binding properties**. Binding properties are optional and whether you specify them depends primarily on whether you target operations that require specific binding properties to be set.  
  
  At a minimum, when you configure the connection to the Siebel system, you only have to specify binding properties and connection parameters that are needed to establish the connection and that affect the metadata returned by the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] for the operations you want to target. However, you might also want to specify values for any additional binding properties and connection parameters that will be used at run time. This is because:  
  
- The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] creates a BizTalk port binding file from the binding properties and connection parameters that you specify when you configure the connection and adds this file to your project.  
  
- The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] creates an app.config file from the binding properties and connection properties that you specify when you configure the connection and adds this file in your project directory.  
  
 
  
## See Also  
 [Get Metadata for Siebel Operations in Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)