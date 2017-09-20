---
title: "Initializing Orchestration Variables | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, variables"
ms.assetid: 770e4e55-1fb9-4b43-854c-63aec5a3c5ba
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Initializing Orchestration Variables
You can initialize the value of a variable by setting it in the Properties window. For example, you can set the **Initial Value** to 32 to initialize the variable of type System.Int32. When adding an initial value to a variable of type string, you must enclose the initial value in quotation marks in the Properties window. If you want the string to contain a quotation mark, use the backslash as an escape character, and use consecutive backslashes when you want a literal backslash in your string. If you do not specify a value for your variables, your variables will be assigned default values as soon as an instance of your orchestration is created.  
  
 If the variable is an instance of a class, you can specify a constructor to initialize it. By default, the **Use Default Constructor** property is set to **True** if a default constructor is available; therefore, the default constructor will be called. If you only intend to use the default constructor, you do not need to initialize the variables again in the **Expression** shape to avoid calling the constructor twice. If the **Use Default Constructor** property is set to **False**, the default constructor will not be called; you must call a constructor in an expression or make an assignment to the variable before you can use it in your orchestration. Moreover, if the constructor requires input parameters, you must set **Use Default Constructor** to **False** and then call the constructor from an **Expression** shape; for example, `myVariable = myNamespace.myClass (param1, param2)`.  
  
 The only circumstance in which you are required to explicitly initialize your variables is when your orchestration contains more than one activate receive, as is possible in a **Scope**, **Parallel Actions**, or **Listen** shape. In this case, automatic initialization is disabled, and you must use an **Expression** shape to initialize your variables. You must place an **Expression** shape after each activation receive, and before any variable is accessed in the orchestration.