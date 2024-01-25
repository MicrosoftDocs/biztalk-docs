---
description: "Learn more about: How to Configure the Terminate Shape"
title: "How to Configure the Terminate Shape"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure the Terminate Shape
![Image that represents the Terminate shape.](../core/media/ebiz-orch-terminate.gif "ebiz_orch_terminate")  
Terminate shape  
  
 The Terminate shape is used to end an orchestration instance. You can specify a message string to accompany the shape when viewed in the output from the Group Hub page.  
  
> [!CAUTION]
>  If you place a **Terminate** shape inside a **Parallel Actions** shape, and the branch with the **Terminate** on it is run, the instance completes immediately, regardless of whether other branches have finished running. Depending on your design, results might be unpredictable in this case.  
  
> [!CAUTION]
>  If a **Terminate** shape is encountered in an orchestration that has been called synchronously (as with the **Call** shape) by another orchestration, the nested instance and all enclosing orchestration instances will be terminated.  
  
### To configure a Terminate shape  
  
-   You can use the **Error Message** property to specify text that you want to associate with the shape when viewed in the query output on the Group Hub page. This text may be a literal string, or an expression that evaluates to a **System.String**.  
  
    > [!CAUTION]
    >  If you enter a literal string, you must enclose it in quotation marks.
