---
title: "Connect to Oracle Database in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 766264c8-bb3f-49e9-b851-1022d1fa5076
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to Oracle Database in Visual Studio
How to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  

## Connection options in Visual Studio

When using [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)], there are several options available to connect to Oracle Database. These options include: 

- The **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** is available in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects. You use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with BizTalk Server, see [Develop BizTalk applications using the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md).  
  
- The **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** is available in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects. You use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with BizTalk Server, see [Develop BizTalk applications using the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md).  
  
  > [!NOTE]
  >  Because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is exposed both as a WCF-Custom binding and as BizTalk adapter, you can use either the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] from a BizTalk project to connect to SQL Server.  
  
- The **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** is available in non-BizTalk programming projects. You use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client class or a WCF service callback interface when you develop solutions using the WCF service model. For more information about developing solutions with the WCF service model, see [Develop Oracle Database applications using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md).  
  
  To use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], you must first connect to the Oracle database. All three methods present a dialog box through which you configure a connection by setting the following:  
  
- **Connection parameters**. These are the parameters that are used to build the connection URI. You must specify a data source (Oracle net service name).  
  
- **User name password credentials for the Oracle database**. These are used to authenticate you on the Oracle database when the connection is established. You must specify a user name and password.  
  
- **Binding properties**. Binding properties are optional at design-time, that is, while generating metadata for operations. For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
  At a minimum, when you configure the connection to the Oracle database, you only have to specify binding properties and connection parameters that are needed to establish the connection and that affect the metadata returned by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] for the operations you want to target. However, you might also want to specify values for any additional binding properties and connection parameters that will be used at run time. This is because:  
  
- The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] creates a BizTalk port binding file from the binding properties and connection parameters that you specify when you configure the connection, and adds this file to your project. Later, you can use this binding file to create a port in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For more information about the binding file, see [Configure a physical port binding using a port binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
- The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] creates an app.config file from the binding properties and connection properties that you specify when you configure the connection, and adds this file in your project directory.  
  

  
## See also  
[Get metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)