---
title: "Connect to SQL Server in Visual Studio using the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62fc2c01-6e4d-4b3b-8581-1d57436ef4e9
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to SQL Server in Visual Studio using the SQL adapter
This section provides instructions about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
- The **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** is available in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects and is installed as part of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. You use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with BizTalk Server, see [Develop BizTalk applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md).  
  
- The **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** is available in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects and is installed as part of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] installation. You use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Develop BizTalk applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md).  
  
  > [!NOTE]
  >  Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is exposed both as a WCF-Custom binding and as BizTalk adapter, you can use either the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] from a BizTalk project to connect to SQL Server.  
  
- The **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** is available in non-BizTalk programming projects. You use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client class or a WCF service callback interface when you develop solutions using the WCF service model. For more information about developing solutions with the WCF service model, see [Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).  
  
  To use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], you must first connect to SQL Server. All three methods present a dialog box through which you configure a connection by setting the following:  
  
- **Connection parameters**. These are the parameters that are used to build the connection URI such as the SQL Server name, the database instance name, and the database name.  
  
- **User name password credentials for SQL Server**. These are used to authenticate you on SQL Server when the connection is established. You must specify a user name and password.  
  
- **Binding properties**. Binding properties are optional, and whether you specify them depends primarily on whether you target operations that require specific binding properties to be set. For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
  At a minimum, when you configure the connection to SQL Server, you only have to specify binding properties and connection parameters that are needed to establish the connection and that affect the metadata returned by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] for the operations you want to target. However, you might also want to specify values for any additional binding properties and connection parameters that will be used at run time. This is because:  
  
- The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] creates a BizTalk port binding file from the binding properties and connection parameters that you specify when you configure the connection and adds this file to your project.  
  
- The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] creates an app.config file from the binding properties and connection properties that you specify when you configure the connection and adds this file in your project directory.  
  
