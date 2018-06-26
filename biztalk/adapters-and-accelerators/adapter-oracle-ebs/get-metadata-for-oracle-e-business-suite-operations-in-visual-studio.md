---
title: "Get metadata for Oracle E-Business Suite operations in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87d7f731-cd0f-4970-a3cd-072f09312989
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Get metadata for Oracle E-Business Suite operations in Visual Studio
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] provides three [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter:  
  
- [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]  
  
- [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]  
  
- [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]  
  
  Adapter clients must use these components to connect to Oracle E-Business Suite, and then generate metadata for the operations they want to perform. All these [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:  
  
- Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.  
  
- Retrieving metadata exposed by the adapter for these target operations.  
  
- Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.  
  
  This section provides instructions about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
> [!NOTE]
>  If you have created a solution using the adapter on a particular version of Oracle E-Business Suite, and now want to deploy the solution on a different version of Oracle E-Business Suite then you should test the solution before deploying it. You might face issues while deploying the solution on a different version of Oracle E-Business Suite because the metadata of the underlying artifact might be different. To resolve this issue, you should regenerate the metadata using the adapter on the same version of Oracle E-Business Suite on which you intend to deploy the solution.  
  
