---
title: "Requirements and Limitations for Expressions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Expression Editor, about Expression Editor"
  - "Expression Editor, requirements"
  - "Orchestration Designer, Expression Editor"
  - "Expression Editor, limitations"
  - "Expression Editor"
  - "Expression Editor, Orchestration Designer"
ms.assetid: 1e0353d3-c2f3-4c10-86e3-8620e62dd0d5
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Requirements and Limitations for Expressions
BizTalk Expression Editor in Orchestration Designer is a standard Visual Studio text editor, which means it offers IntelliSense. You use BizTalk Expression Editor to enter an expression in textual form.  
  
 Use the text box to enter a single expression in textual form. The expression can span multiple lines, but must end with single semicolon.  
  
 The following is a list of limitations when using expressions in the BizTalk Expression Editor:  
  
- Compound assignment such as "+=", "-=", or "*=" is not supported.  
  
- More than one assignment operator in a statement is not supported.  
  
- Assignment within an “if” or “while” predicate is not supported.  
  
- Increment and decrement are not supported. For example, "++" and "--".  
  
- For message parts, member access is allowed on public methods, nested types, static data fields, read-only .NET properties when annotated with Microsoft.XLANGs.BaseTypes.DistinguishedFieldAttribute, all public data fields, and non-read-only .NET properties.  
  
- Indexers or parameterized .NET properties are not supported.  
  
- Delegates and events are not supported.  
  
- Generics are not supported.  
  
- Flow control syntax such as "foreach", "for", "do-while", "break", and "continue" are not supported.  
  
- Ternary operations are not supported. For example, "?:".  
  
- You can add comments in the Expression shape, but the Expression shape must contain at least one statement.  
  
- Arrays are not supported.  
  
- When the Expression shape is placed in a Construct Message shape, you cannot do any control flow. For example, "if-then-else" or "while".  
  
- All valid expression statements are of the form:  
  
  -   Dotted-name = expression;  
  
  -   Dotted-name = expression;  
  
  Though you can use BizTalk Expression Editor to enter complex expressions easily and quickly, you cannot use it to enter an arbitrary amount of code. The reason for this is to keep code for the business process separate from its implementation code.