---
description: "Learn more about: Error - Type Name Not Valid"
title: "Error - Type Name Not Valid"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.typeNameNotValid"
---
# Error - Type Name Not Valid
**Error Code**  
  
 BEC2011  
  
 **Explanation**  
  
 The **Type Name** property of this schema file is not valid. Because the value of the **Type Name** property is used as the name of an automatically generated C# class name, it must be a valid C# identifier and cannot be a reserved BizTalk keyword.  
  
 **User Action**  
  
 Select the relevant schema file in Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, and then in the Properties window, change the **Type Name** property to a value that is a valid C# identifier and is not a reserved BizTalk keyword.
