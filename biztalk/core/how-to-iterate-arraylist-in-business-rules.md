---
title: "How to Iterate ArrayList in Business Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Business Rules Framework, ArrayList"
  - "business rules, arrays"
  - "Business Rules Framework, programming"
ms.assetid: 935e8648-72dc-4128-986c-72b0487bc074
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Iterate ArrayList in Business Rules
This section provides an example of iterating through members of an **ArrayList** in business rules.  
  
 Assume you have an **ArrayList** with a collection of **MyClass** objects. Your business rules would look like the following.  
  
## Rule A  
 IF 1==1  
  
 THEN Assert (ArrayList.GetEnumerator)  
  
 An **IEnumerator** type is asserted into the working memory, because the rule condition (1==1) always evaluates to true.  
  
## Rule B  
 IF IEnumerator.MoveNext  
  
 THEN    Assert (IEnumerator.get_Current)  
  
 Update (IEnumerator)  
  
 As the rule iterates through the **ArrayList**, each **MyClass** object in the collection is asserted into the working memory.  
  
## Rule C  
 IF MyClass.MyProperty==2  
  
 THEN \<Do Something...>  
  
 This rule executes action(s) when the property value of the object is matched in the condition.