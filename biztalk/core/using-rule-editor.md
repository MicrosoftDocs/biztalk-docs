---
title: "Using Rule Editor | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Rule Editor [Business Rule Composer], about Rule Editor"
  - "Rule Editor [Business Rule Composer], Conditions Editor"
  - "Business Rule Composer, Rule Editor"
  - "Rule Editor [Business Rule Composer], Actions Editor"
  - "Rule Editor [Business Rule Composer]"
ms.assetid: 6559a8d1-6caf-4c6e-ac80-acaa4eb57938
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Rule Editor
Use the Rule Editor to view and edit conditions in the Conditions Editor and actions in the Actions Editor for the selected rule.  
  
## Conditions Editor  
 Use the Conditions Editor (part of the Rule Editor) to view and edit conditions for firing rules. You can add built-in predicates by using the shortcut menu, drag items from the Facts Explorer to define arguments and predicates, and enter argument values inline by clicking an argument link.  
  
 Use the shortcut menu to access the following options.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Add logical AND**|Add an operator to combine two or more predicates to form a logical **AND** expression.|  
|**Add logical OR**|Add an operator to combine two or more predicates to form a logical **OR** expression.|  
|**Add logical NOT**|Add the operator **NOT** to negate a logical expression or predicate.|  
|**Predicates**|Add a predicate expression based on one of the built-in predicates provided by the Rule object model, such as the **Is Equal To** operator.|  
|**Predicates \ After**|Represent the temporal predicate that answers the question "Is time1 chronologically after time2"?|  
|**Predicates \ Before**|Represent the temporal predicate that answers the question "Is time1 chronologically before time2."|  
|**Predicates \ Between**|Represent the temporal predicate that answers the question "Is time1 chronologically between time2 and time3."|  
|**Predicates \ Equal**|Represent the relational equality operator.|  
|**Predicates \ Exists**|Represent the XML element or attribute existence predicate used in rule conditions.|  
|**Predicates \ GreaterThan**|Represent the relational greater than operator.|  
|**Predicates \ GreaterThanEqual**|Represent the relational greater than or equal to operator.|  
|**Predicates \ LessThan**|Represent the relational less than operator.|  
|**Predicates \ LessThanEqual**|Represents the relational less than or equal to operator.|  
|**Predicates \ Match**|Determines if a regular expression is present in a specified input string.|  
|**Predicates \ NotEqual**|Represent the relational inequality operator.|  
|**Predicates \ Range**|Test whether a value is between a range.|  
|**Delete logical operator**|Delete the selected logical operator (**AND**, **OR**, or **NOT**).|  
|**Delete predicate**|Delete the selected predicate.|  
|**Move Up**|Move the predicate up one position or a level.|  
|**Move Down**|Move the predicate down one position or a level.|  
|**Go to vocabulary**|Locate the vocabulary definition in the Facts Explorer that corresponds to the selected predicate or argument.|  
|**Go to source fact**|Locate the XML element, database column, or .NET method in the Facts Explorer that corresponds to the selected predicate or argument.|  
|**Reset argument**|Delete the selected argument (and any nested arguments), and restore the initial definition.|  
|**Set to null**|Replace the selected argument with a null constant definition.|  
|**Set to empty string**|Replace the selected argument with an empty string value.|  
  
## Actions Editor  
 Use the Actions Editor (part of the Rule Editor) to view and edit actions to execute when a rule is fired. You can add built-in actions by using the shortcut menu, drag items from the Facts Explorer to define actions and arguments, and enter argument values inline by clicking an argument link.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Delete action**|Delete the selected action.|  
|**Go to vocabulary**|Locate the vocabulary definition in the Facts Explorer that corresponds to the selected action or argument.|  
|**Go to source fact**|Locate the XML element, database column, or .NET method in the Facts Explorer that corresponds to the selected action or argument.|  
|**Move Up**|Move the action up one position or a level.|  
|**Move Down**|Move the action down one position or a level.|  
|**Reset argument**|Delete the selected argument (and any nested arguments), and restore the initial definition.|  
|**Set to null**|Replace the selected argument with a null constant definition.|  
|**Set to empty string**|Replace the selected argument with an empty string value.|  
|**Functions**|Add an argument based on one of the built-in functions provided by the Rule object model, such as the **Add** operator.|  
|**Assert**|Add a new fact into the working memory of the rule engine instance.|  
|**Retract**|Remove a fact from the working memory of the rule engine instance.|  
|**RetractByType**|Remove a fact of specified type from the working memory of the rule engine instance.|  
|**Clear**|Reset the working memory and agenda of the rule engine instance.|  
|**Halt**|Terminate the rule processing.|  
|**Update**|Update a fact in the working memory of the rule engine instance.|  
  
## Output window  
 Use the Output window to view results of test execution for a selected policy version.  
  
 Use the shortcut menu to access the following options.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Clear All**|Clear all text from the Output window.|  
|**Copy**|Copy the selected text in the Output window to the Clipboard.|  
|**Select All**|Select all the text contained in the Output window.|  
|**Save to File**|Save the text contained in the Output window to a specified file.|