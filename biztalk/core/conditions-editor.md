---
title: "Conditions Editor | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.bre.conditions"
helpviewer_keywords: 
  - "Business Rule Composer, Conditions Editor"
  - "Conditions Editor [Business Rule Composer]"
ms.assetid: 4bc3780f-7a5b-401d-93a2-38fd82aeab4d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Conditions Editor
Use the **Conditions Editor** (part of the Rule Editor) to view and edit conditions for firing rules. You can add built-in predicates using the shortcut menu, drag items from the Facts Explorer to define arguments and predicates, and enter argument values inline by clicking an argument link.  
  
 Use the shortcut menu to access the following options.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Add logical AND**|Add an operator to combine two or more predicates to form a logical-**AND** expression.|  
|**Add logical OR**|Add an operator to combine two or more predicates to form a logical-**OR** expression.|  
|**Add logical NOT**|Add the operator **NOT** to negate a logical expression or predicate.|  
|**Predicates**|Add a predicate expression based on one of the built-in predicates provided by the Rule Object Model, such as the **Is Equal To** operator.|  
|**Delete logical operator**|Delete the selected logical operator (**AND**, **OR**, or **NOT**).|  
|**Delete predicate**|Delete the selected predicate.|  
|**Move Up**|Move the predicate up one position or a level.|  
|**Move Down**|Move the predicate down one position or a level.|  
|**Go to vocabulary**|Locate the vocabulary definition in the Facts Explorer that corresponds to the selected predicate or argument.|  
|**Go to source fact**|Locate the XML element, database column, or .NET method in the Facts Explorer that corresponds to the selected predicate or argument.|  
|**Reset argument**|Delete the selected argument (and any nested arguments), and restore the initial definition.|  
|**Set to null**|Replace the selected argument with a null constant definition.|  
|**Set to empty string**|Replace the selected argument with an empty string value.|  
  
## See Also  
 [How to Create Vocabulary Definitions](../core/how-to-create-vocabulary-definitions.md)   
 [Windows of the Business Rule Composer](../core/windows-of-the-business-rule-composer.md)