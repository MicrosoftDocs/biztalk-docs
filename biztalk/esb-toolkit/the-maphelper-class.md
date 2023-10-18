---
description: "Learn more about: The MapHelper Class"
title: "The MapHelper Class"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The MapHelper Class
Use the **MapHelper** class to perform transformations directly without using the transformation Web service.  
  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] installer installs and registers the assembly **Microsof.Practices.ESB.Transform.dll** with the **MapHelper** class in the global assembly cache.  
  
 The **MapHelper** class exposes two public methods:  
  
-   **TransformMessage**. This method takes as parameters a string that contains the message to transform and a string that contains the fully qualified name of a map deployed in BizTalk. The method returns a string containing the transformed document.  
  
-   **TransformMessageStream**. This method takes as parameters a stream that contains the message to transform and a string that contains the fully qualified name of a map deployed in BizTalk. The method returns a string that contains the transformed document.
