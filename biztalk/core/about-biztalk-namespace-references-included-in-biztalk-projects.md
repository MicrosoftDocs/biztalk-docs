---
title: "About BizTalk Namespace References Included in BizTalk Projects | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Xml namespace"
  - "Microsoft.BizTalk.GlobalPropertySchemas namespace"
  - "namespaces, System.Xml namespace"
  - "System namespace"
  - "namespaces, System namespace"
  - "namespaces, Microsoft.BizTalk.GlobalPropertySchemas namespace"
  - "Microsoft.BizTalk.DefaultPipelines namespace"
  - "projects, namespaces"
  - "namespaces, warnings"
  - "namespaces, Microsoft.BIzTalk.DefaultPipelines namespace"
  - "namespaces"
ms.assetid: cb642eac-7307-44f8-bbba-3ae364e11ea2
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# About BizTalk Namespace References Included in BizTalk Projects
When you add a new BizTalk project, the following namespaces are included by default:  
  
- **Microsoft.BizTalk.DefaultPipelines**  
  
- **Microsoft.BizTalk.GlobalPropertySchemas**  
  
- **System**  
  
- **System.Xml**  
  
  You can also add new references and Web references to your project. For more information about adding references using the **Project** menu, see [Using Visual Studio](../core/using-visual-studio.md). For information about adding Web references, see [Adding Web References](../core/adding-web-references.md).  
  
> [!CAUTION]
>  Do not remove the default references. If you remove the default references, you might encounter problems when referencing BizTalk items in your project. You can restore default references in Solution Explorer.  
  
> [!CAUTION]
>  If your BizTalk project references another assembly, and that assembly is updated, the updates or changes are not automatically picked up in your BizTalk project. You should remove the outdated reference in Solution Explorer, and then add the reference back (re-reference the assembly). Alternatively, you can close your solution and reopen it. In either case, the latest updates to the referenced assembly are available to your project.  
  
## In This Section  
  
-   [Microsoft.BizTalk.DefaultPipelines Reference](../core/microsoft-biztalk-defaultpipelines-reference.md)  
  
-   [Microsoft.BizTalk.GlobalPropertySchemas Reference](../core/microsoft-biztalk-globalpropertyschemas-reference.md)  
  
-   [System Reference](../core/system-reference.md)  
  
-   [System.Xml Reference](../core/system-xml-reference.md)