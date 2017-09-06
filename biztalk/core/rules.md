---
title: "Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "business rules, actions"
  - "Business Rules Engine, business rules"
  - "business rules, about business rules"
  - "business rules, conditions"
  - "business rules, facts"
  - "business rules"
ms.assetid: b288dd07-33f1-42fe-bbfb-02674ef3b3ca
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Rules
Business rules are declarative statements that govern the conduct of business processes. A rule consists of a condition and actions. The condition is evaluated, and if it evaluates to **true**, the rule engine initiates one or more actions.  
  
 Rules in the Business Rules Framework are defined by using the following format:  
  
 IF`condition` THEN`action`  
  
 Consider the following example:  
  
 IF amount is less than or equal to available funds  
  
 THEN conduct transaction and print receipt  
  
 This rule determines whether a transaction will be conducted by applying business logic, in the form of a comparison of two monetary values, to data or facts, in the form of a transaction amount and available funds.  
  
 You can use the Business Rule Composer to create, modify, version, and deploy business rules. Alternatively, you can perform the preceding tasks programmatically.  
  
## Conditions  
 A condition is a true/false (Boolean) expression that consists of one or more predicates that are applied to facts.  
  
 In our example, the predicate **less than or equal to** is applied to the facts **amount** and **available funds**. This condition will always evaluate to either **true** or **false**.  
  
 Predicates can be combined with the logical operators **AND**, **OR**, and **NOT** to form a logical expression that is potentially quite large, but will always evaluate to either **true** or **false**.  
  
## Actions  
 Actions are the functional consequences of condition evaluation. If a rule condition is met, a corresponding action or actions are initiated.  
  
 In our example, "conduct transaction" and "print receipt" are actions that are carried out when, and only when, the condition (in this case, "IF amount is less than or equal to available funds") is true.  
  
 Actions are represented in the Business Rules Framework by invoking methods or setting properties on objects, or by performing set operations on XML documents or database tables.  
  
## Facts  
 Facts are the data upon which rules operate. In our example, "amount" and "available funds" are facts. For more information, see [Facts](../core/facts.md).  
  
## See Also  
 [How to Create Policies and Rules](../core/how-to-create-policies-and-rules.md)