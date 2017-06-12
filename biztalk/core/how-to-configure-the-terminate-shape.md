---
title: "How to Configure the Terminate Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Terminate shape [Orchestration Designer], about Terminate shape"
  - "Terminate shape [Orchestration Designer], literal strings"
  - "configuring [Orchestration Designer], Terminate shapes"
  - "Terminate shape [Orchestration Designer], configuring"
  - "Terminate shape [Orchestration Designer]"
ms.assetid: 2c4f2c94-2bab-4af3-8954-7275696ca147
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Terminate Shape
![](../core/media/ebiz-orch-terminate.gif "ebiz_orch_terminate")  
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