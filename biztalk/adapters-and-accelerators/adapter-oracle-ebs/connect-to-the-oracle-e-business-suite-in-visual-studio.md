---
title: "Connect to the Oracle E-Business Suite in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e290ea7e-03f3-49d4-9f18-1e539d727d9c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to the Oracle E-Business Suite in Visual Studio
This section provides information about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
- The **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** is available in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects. You use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with BizTalk Server, see [Developing BizTalk Server Applications](../../core/developing-biztalk-server-applications.md).  
  
- The **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** is available in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projects. You use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with BizTalk Server, see [Developing BizTalk Server Applications](../../core/developing-biztalk-server-applications.md).  
  
  > [!NOTE]
  >  Because the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is exposed both as a WCF-Custom binding and as BizTalk adapter, you can use either the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] from a BizTalk project to connect to Oracle E-Business Suite.  
  
- The **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** is available in non-BizTalk programming projects. You use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client class or a WCF service callback interface when you develop solutions using the WCF service model. For more information about developing solutions with the WCF service model, see [Develop Oracle E-Business Suite applications using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md).  
  
  To use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], you must first connect to the Oracle E-Business Suite. All three methods present a dialog box through which you configure a connection by setting the following:  
  
- **Connection parameters**. These are the parameters that are used to build the connection URI. You must specify a data source (Oracle net service name).  
  
- **User name password credentials for the Oracle E-Business Suite**. These are used to authenticate you on the Oracle E-Business Suite when the connection is established. You must specify a user name and password.  
  
  > [!IMPORTANT]
  >  At this stage, you can specify the credentials for the Oracle E-Business Suite or the underlying Oracle database. To connect and generate metadata you can specify any credentials. However, while performing operation to invoke an Oracle E-Business Suite artifact, you must specify the Oracle E-Business Suite credentials because they are required to set the application context for the Oracle E-Business Suite application you want to invoke. For more information about setting applications context, see [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
- **Binding properties**. Binding properties are optional at design-time, that is, while generating metadata for operations. For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
  At a minimum, when you configure the connection to the Oracle database, you only have to specify binding properties and connection parameters that are needed to establish the connection and that affect the metadata returned by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] for the operations you want to target. However, you might also want to specify values for any additional binding properties and connection parameters that will be used at run time. This is because:  
  
- The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] creates a BizTalk port binding file from the binding properties and connection parameters that you specify when you configure the connection, and adds this file to your project. Later, you can use this binding file to create a port in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For more information about the binding file, see [Configure a physical port binding using a port binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
- The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] creates an app.config file from the binding properties and connection properties that you specify when you configure the connection, and adds this file in your project directory.  
  

- [Connect to Oracle E-Business Suite in Visual Studio using Add Adapter Service Reference Plug-in](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-service-reference.md)  
  
## See Also  
 [Get metadata for Oracle E-Business Suite operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)