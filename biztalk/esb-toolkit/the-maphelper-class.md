---
title: "The MapHelper Class | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c552c066-835f-4515-939f-dd465a7a5ed0
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The MapHelper Class
Use the **MapHelper** class to perform transformations directly without using the transformation Web service.  
  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] installer installs and registers the assembly **Microsof.Practices.ESB.Transform.dll** with the **MapHelper** class in the global assembly cache.  
  
 The **MapHelper** class exposes two public methods:  
  
-   **TransformMessage**. This method takes as parameters a string that contains the message to transform and a string that contains the fully qualified name of a map deployed in BizTalk. The method returns a string containing the transformed document.  
  
-   **TransformMessageStream**. This method takes as parameters a stream that contains the message to transform and a string that contains the fully qualified name of a map deployed in BizTalk. The method returns a string that contains the transformed document.