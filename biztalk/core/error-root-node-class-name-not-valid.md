---
description: "Learn more about: Error - Root Node Class Name Not Valid"
title: "Error - Root Node Class Name Not Valid"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.rootNodeClassNameNotValid"
---
# Error - Root Node Class Name Not Valid
**Error Code**  
  
 BEC2012  
  
 **Explanation**  
  
 The **RootNode TypeName** property of one of the root nodes in this schema is not valid. Because the value of the **RootNode TypeName** property is used as the name of an automatically generated C# class name, it must be a valid C# identifier and cannot be a reserved BizTalk keyword.  
  
 **User Action**  
  
 Select the indicated root node, and then in the Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, change the **RootNode TypeName** property to a value that is a valid C# identifier and is not a reserved BizTalk keyword.
