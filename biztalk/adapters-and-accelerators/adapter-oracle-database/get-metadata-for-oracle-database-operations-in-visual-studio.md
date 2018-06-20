---
title: "Get metadata for Oracle Database operations in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "metadata, retrieving in Visual Studio"
  - "metadata"
ms.assetid: d903b408-1144-4625-909d-710826e37769
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Get metadata for Oracle Database operations in Visual Studio
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] provides three [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter.  
  
- The [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] and the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] are available in BizTalk Server projects. You use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] and the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution. For more information about developing solutions with BizTalk Server, see [Develop BizTalk applications using the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)  
  
- The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] is available in non-BizTalk programming projects. You use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client class or a WCF service callback interface when you develop solutions using the WCF service model. For more information about developing solutions with the WCF service model, see [Develop Oracle Database Applications using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md).  
  
  All these three [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:  
  
- Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.  
  
- Retrieving metadata exposed by the adapter for these target operations.  
  
- Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.  
  
  This section provides instructions about how to use [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
## In This Section  
  
-   [Connect to the Oracle Database in Visual Studio using the Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md) 
  
-   [Browse, search, and get metadata for Oracle Database operations](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md)  
  
## See Also  
[Develop your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)