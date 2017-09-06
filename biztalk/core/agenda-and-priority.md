---
title: "Agenda and Priority | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "business rules, executing"
  - "Business Rules Engine, agendas"
  - "Business Rules Engine, priorities"
  - "business rules, priorities"
  - "business rules, examples"
  - "Business Rules Engine, examples"
  - "examples, Business Rules Engine"
  - "Business Rules Engine, rules"
ms.assetid: ca54f750-4f2d-4734-8e6e-7af1b4967e6a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Agenda and Priority
To understand how the Business Rule engine evaluates rules and executes actions, you need to understand the concepts of *agenda* and *priority*.  
  
## Agenda  
 The agenda is a schedule used by the engine to queue rules for execution. The agenda exists for an engine instance, and acts on a single policy, not on a series of policies. When a fact is asserted into working memory and the conditions of a given rule are satisfied, the rule is placed on the agenda and executed according to priority. A rule's actions are executed in order from top to bottom, and then the actions of the next rule on the agenda are executed.  
  
 The actions belonging to a rule are treated as a block, so that all actions are executed before moving on to the next rule. All actions in a rule block will execute regardless of other actions in the block. For more information about assertion, see [Engine Control Functions](../core/engine-control-functions.md).  
  
 The following example demonstrates how the agenda works.  
  
 **Rule1**  
  
```  
IF  
Fact1 == 1  
THEN  
Action1  
Action2  
```  
  
 **Rule2**  
  
```  
IF  
Fact1 > 0  
THEN  
Action3  
Action4  
```  
  
 We assert the fact Fact1, which has a value of 1, into the engine. Because the conditions of both Rule 1 and Rule 2 are satisfied, both rules are moved to the agenda for execution of their actions.  
  
|Working memory|Agenda|  
|--------------------|------------|  
|Fact1 (value=1)|**Rule1**<br /><br /> -   Action1<br />-   Action2<br /><br /> **Rule2**<br /><br /> -   Action3<br />-   Action4|  
  
## Priority  
 Priority for execution is set on each individual rule, with a default priority of 0 for all rules. The priority can range on either side of 0, with larger numbers having higher priority. Actions are executed in order from highest priority to lowest priority.  
  
 The following example shows how priority affects the order of execution for the rules.  
  
 **Rule1 (priority = 0)**  
  
```  
IF  
Fact1 == 1  
THEN  
Discount = 10%  
```  
  
 **Rule2 (priority = 10)**  
  
```  
IF  
Fact1 > 0  
THEN  
Discount = 15%  
```  
  
 The conditions for both rules have been met, but Rule2 is executed first because it has higher priority. The final discount is 10 percent, because it is the result of the action executed for Rule1, as shown in the following table.  
  
|Working memory|Agenda|  
|--------------------|------------|  
|Fact1 (value=1)|**Rule2**<br /><br /> Discount = 15%<br /><br /> **Rule1**<br /><br /> Discount = 10%|  
  
## See Also  
 [Rule Engine](../core/rule-engine.md)