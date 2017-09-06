---
title: "How to Modify Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "business rules, activating"
  - "deactivating business rules"
  - "business rules, priorities"
  - "activating business rules"
  - "business rules, deactivating"
  - "modifying, business rules"
  - "business rules, modifying"
ms.assetid: 661b2637-b5d6-4bde-9c42-24cd9e9d241c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Modify Rules
The ability to change rules is an important part of the business rules paradigm. You can modify rules within a policy in two ways: either by creating a new version of the policy, or by directly modifying an unpublished version of the policy.  
  
 You can modify rules individually, add new rules, or delete existing rules. You can delete predicates and logical operators from a rule condition, delete actions, move actions up and down in the display, or move predicates and logical operators within a condition. Keep in mind, however, the order in which the predicates and logical operators are displayed does not determine the order of evaluation.  
  
 You can set a rule to be inactive, so that the rule is not executed when the policy is executed, or you can reactivate a rule that has been deactivated.  
  
 You can set the priority on a rule so that its actions will be executed before or after the actions of any rule of different priority.  
  
> [!CAUTION]
>  If you need to stop your SQL Server computer, be sure to save any unsaved vocabulary versions or vocabulary definitions, and close the Business Rule Composer so that no changes are lost.  
  
 This topic contains procedures for the following tasks:  
  
-   To change an argument in a condition or action  
  
-   To move a predicate within a condition  
  
-   To move a logical operator within a condition  
  
-   To change the order of actions within a rule  
  
-   To delete a predicate, logical operator, or action  
  
-   To activate or deactivate a rule  
  
-   To set a priority on a rule  
  
### To change an argument in a condition or action  
  
1.  In the Facts and Definitions window, click the appropriate tab, and navigate to the term you want to use as an argument. The term must be of a type expected by the predicate or function.  
  
2.  Click the term and drag it onto a predicate argument in a condition or a function argument in an action.  
  
### To move a predicate within a condition  
  
-   Click the predicate, and drag it to another logical operator.  
  
### To move a logical operator within a condition  
  
-   Click the logical operator, and drag it onto another logical operator or onto **Conditions**.  
  
### To change the order of actions within a rule  
  
-   Click the action and then click **Move action up** or **Move action down**.  
  
    > [!NOTE]
    >  The actions of a rule will be executed in the order specified with the exception of engine control functions which are executed after the other actions.  
  
### To delete a predicate, logical operator, or action  
  
-   Click the predicate, logical operator, or action, and then click **Delete**.  
  
### To activate or deactivate a rule  
  
-   Click the rule, and then in the Properties window, set **Active** to either **True** or **False**.  
  
### To set a priority on a rule  
  
-   Click the rule, and then in the Properties window, set **Priority** to an integer value.  
  
    > [!NOTE]
    >  Priorities are relative, and all of the actions of a rule of a given priority will be executed in order before any of the actions of a rule with a lower value for priority. The priority value defaults to zero, but it can be positive or negative.