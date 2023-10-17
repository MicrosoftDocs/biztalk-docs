---
description: "Learn more about: How to Configure the Suspend Shape"
title: "How to Configure the Suspend Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [Orchestration Designer], Suspend shapes"
  - "Suspend shape [Orchestration Designer], literal strings"
  - "Suspend shape [Orchestration Designer], configuring"
  - "Suspend shape [Orchestration Designer]"
  - "atomic transactions, Suspend shape [Orchestration Designer]"
  - "Suspend shape [Orchestration Designer], atomic transactions"
  - "Suspend shape [Orchestration Designer], about Suspend shape"
ms.assetid: 62fbb6d4-78d2-4671-84bb-909cbf6b0ec3
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Suspend Shape
![Image that represents the Suspend shape.](../core/media/ebiz-orch-suspend.gif "ebiz_orch_suspend")  
Suspend shape  
  
 When an orchestration instance is suspended, an error is logged. You can specify a message string to accompany the error to help the administrator diagnose the situation.  
  
 All of the state information for the orchestration instance is saved, and is reinstated if and when the administrator resumes the orchestration instance.  
  
> [!NOTE]
>  If a **Suspend** shape exists in an orchestration that has been called synchronously (as with the **Call** shape) by another orchestration, the nested instance and all enclosing orchestration instances will be suspended.  
  
> [!NOTE]
>  You cannot place a **Suspend** shape inside an atomic transaction.  
  
### To configure a Suspend shape  
  
-   You can use the **Error Message** property to specify text that you want to be logged when a **Suspend** shape is encountered. This text may be a literal string, or an expression that evaluates to a **System.String**.  
  
    > [!CAUTION]
    >  If you enter a literal string, you must enclose it in quotation marks.
