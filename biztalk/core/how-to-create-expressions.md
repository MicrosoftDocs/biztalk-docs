---
title: "How to Create Expressions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, expressions [Expression Editor]"
  - "opening, Expression Editor [Orchestration Designer]"
  - "Expression Editor, opening"
  - "editing, expressions [Expression Editor]"
  - "Expression Editor, editing expressions"
  - "Expression Editor, creating expressions"
ms.assetid: 48f8b00f-6ef1-4145-ad17-15c95518fc8a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Expressions
BizTalk Expression Editor enables you to create XLANG/s expressions to expand the capabilities of various Orchestration Designer shapes. You can create XLANG/s expressions to make decisions, set delays, make .NET calls, and test while loop conditions.  
  
 It enables you to assign values to messages or message parts in the Message Assignment shape, and to make .NET calls and manipulate the values of variables in the **Expression** shape. You can also use it to construct complex Boolean expressions in the **Loop** and **Decide** shapes, and to set a delay in the **Delay** shape.  
  
### To open BizTalk Expression Editor  
  
1.  Right-click an **Expression** shape, a **Loop** shape, a **Message Assignment** shape, a **Delay** shape, or a branch of a **Decide** shape.  
  
2.  Click **Edit Expression**.  
  
3.  BizTalk Expression Editor appears.  
  
### To create or edit an expression  
  
1.  Type or edit the expression in the text field of BizTalk Expression Editor.  
  
2.  Click OK. This saves the expression and applies it to the selected shape.  
  
## See Also  
 [XLANG-s Language](../core/xlang-s-language.md)