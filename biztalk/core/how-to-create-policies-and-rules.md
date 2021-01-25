---
description: "Learn more about: How to Create Policies and Rules"
title: "How to Create Policies and Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, business rules"
  - "policies, rules"
  - "policies, predicates"
  - "business rules, creating"
  - "creating, policies"
  - "policies, logical operators"
  - "policies, examples"
  - "policies, default actions"
  - "policies"
  - "policies, arguments"
  - "policies, creating"
ms.assetid: 59f06a67-edde-443b-9fbb-55ec4429837a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Policies and Rules
You can create rules with conditions that are logical groupings of logical operators (**AND**, **OR**, and **NOT**) applied to predicates (built-in or user-defined functions or operators) that take arguments (built-in or user-defined fact references). You can also right-click **Conditions** or logical operators and select a logical operator or built-in predicate from the context menu.  
  
 You can define actions (built-in or user-defined functions) to be executed if the rule condition evaluates to **true**.  
  
> [!NOTE]
>  If you include more than one predicate in a rule, all predicates must appear as arguments to a logical operator. (The top level can be a single .NET member, db column, or XML field/attribute that is of boolean type.)  
  
### To create a policy  
  
1.  In the Policy Explorer pane, right-click **Policies**, and then click **Add New Policy**.  
  
     A new folder, **Policy1**, is created under **Policies**. By default, version 1 of a new policy is created for you.  
  
2.  Click **Policy1**.  
  
3.  In the Name property pane, type a name.  
  
### To add a rule to a policy version  
  
-   In the Policy Explorer pane, expand [**your policy**], right-click **Version 1.0 (not saved)**, and then select **Add New Rule**.  
  
### To add a logical operator to a rule condition  
  
-   In the Rule Definition window, right-click **Conditions**, and then click one of **Add Logical AND**, **Add Logical OR**, or **Add Logical NOT**.  
  
### To add a built-in predicate to a rule condition or logical operator  
  
1.  In the Facts Explorer window, click the **Vocabularies** tab, and then click the **Predicates** folder.  
  
2.  Expand a published version of a predicate vocabulary, and click the predicate you want.  
  
3.  Drag the predicate onto the logical operator, or onto **Conditions** if your rule will contain only one predicate.  
  
    > [!NOTE]
    >  You can also add a predicate directly from a data source, provided that the data element acts as a predicate (evaluates to **true** or **false**).  
  
### To add a built-in action to a rule  
  
1.  In the Facts Explorer window, click the **Vocabularies** tab, and then click the **Functions** folder.  
  
2.  Expand a published version of the function vocabulary, and click the function you want.  
  
3.  Drag the function onto **Actions**. You can also right-click **Actions**, and select a built-in action from the context menu.  
  
### To add an argument to a condition or action  
  
1.  In the Facts Explorer window, click the **Vocabularies** tab, and then click a vocabulary folder.  
  
2.  Expand a published version of the vocabulary, and click the term you want. The term must be of a type expected by the predicate or function.  
  
3.  Drag the term onto a predicate argument in a condition or a function argument in an action.  
  
    > [!NOTE]
    >  You can also add an argument directly from a data source or in the case of XML you can specify the field type in the properties when selecting a field; this must of course be compatible with the data itself , provided that the data element is of a type expected by the predicate or action. To add an argument directly from a data source, click the appropriate tab in the Facts Explorer window, navigate to the item you want, and drag it onto a predicate argument or function argument.  
  
    > [!NOTE]
    >  You can add a constant value to an argument directly by clicking the argument and entering the constant value you want.
