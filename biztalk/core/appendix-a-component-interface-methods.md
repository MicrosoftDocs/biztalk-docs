---
description: "Learn more about: Appendix A: Component Interface Methods"
title: "Appendix A: Component Interface Methods | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "component interfaces, methods"
  - "methods, component interfaces"
  - "component interface methods"
ms.assetid: c8377589-fbdf-4287-b822-53263a00381d
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Appendix A: Component Interface Methods
Microsoft BizTalk Adapter for PeopleSoft Enterprise provides standard methods for component interfaces.  
  
> [!NOTE]
>  The `interactiveMode` parameter, in the Ex-version of the methods, assists in debugging a call to the back-end (`Create/CreateEx`, `Update/UpdateEx`, and `DeleteOnly`). Each item in the *Ex call to the back-end is called separately, so you know exactly which item failed. There is a decrease in performance when you use an \*Ex method because each property's item receives a separate call. You can develop with \*Ex method and then switch to the main method (for example, `Create`) for production. You can also use a debug switch at production to switch between using the method and the \*Ex method.  
  
## In This Section  
  
-   [CreateEx Method](../core/createex-method.md)  
  
-   [DeleteOnly Method](../core/deleteonly-method.md)  
  
-   [Find Method](../core/find-method.md)  
  
-   [Get Method](../core/get-method.md)  
  
-   [UpdateEx Method](../core/updateex-method.md)  
  
-   [Component Interface User-Defined Methods](../core/component-interface-user-defined-methods.md)  
  
-   [Effective Date Properties](../core/effective-date-properties.md)
