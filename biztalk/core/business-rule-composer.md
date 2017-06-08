---
title: "Business Rule Composer | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.bre.composer.main"
helpviewer_keywords: 
  - "creating, policies"
  - "Business Rule Composer, about Business Rule Composer"
  - "policies, modifying"
  - "modifying, policies"
  - "policies, creating"
ms.assetid: 9f4f2d94-ad13-4ec7-a938-fd0ab4be4e0a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Business Rule Composer
You can use the **Business Rule Composer** to create and edit policies (or rule sets), and vocabularies to express rules in natural language.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Policy Explorer**|Manage policies and rules in the rule store.|  
|**Facts Explorer**|Manage vocabularies and browse through fact data types (databases, XML schemas, and .NET classes).|  
|**Facts Explorer, Vocabularies** tab|Create, modify, delete, and publish vocabulary versions and definitions; drag published vocabulary definitions onto the Conditions Editor or Actions Editor to define arguments and actions in a rule definition.|  
|**Facts Explorer, XML Schemas** tab|Browse through XSD schemas for the definitions of XML elements and attributes; drag items onto the Conditions Editor or Actions Editor to define predicates, actions, and arguments.|  
|**Facts Explorer, Databases** tab|Browse through database servers for databases and table definitions; drag items onto the Conditions Editor or Actions Editor to define predicates, actions, and arguments.|  
|**Facts Explorer, .NET Classes** tab|Browse through .NET assemblies for public .NET class definitions; drag items onto the Conditions Editor or Actions Editor to define predicates, actions, and arguments.|  
|**Properties** window|View and edit properties of a selected item in the Policy Explorer, Facts Explorer, Conditions Editor, or Actions Editor.|  
|**Policy Instructions** page|View Quick Start Help for using the Rule Composer.|  
|**Rule Editor**|View and edit conditions in the Conditions Editor and actions in the Actions Editor for the selected rule.|  
|**Conditions Editor**|View and edit conditions for firing rules. Add built-in predicates using the shortcut menu, drag items from the Facts Explorer to define arguments and predicates, or enter argument values inline by clicking an argument link.|  
|**Actions Editor**|View and edit actions to be executed upon corresponding rule firings. Add built-in actions using the shortcut menu, drag items from the Facts Explorer to define actions and arguments, or enter argument values inline by clicking an argument link.|  
|**Vocabulary Definition Wizard**|Define a business term for use in a vocabulary.|  
|**Value Type** page|Specify whether you want to use a constant value, a range of values, or a set of values.|  
|**Define a Constant Value** page|Define a constant with a type and a value.|  
|**Define a Set of Values** page|Define a set of values consisting of constants or other vocabulary definitions.|  
|**Define a Range of Values** page|Define a range of values with a type, a display format, and high and low range values.|  
|**.NET Class Definition** page|Specify a definition for a .NET class or .NET class member.|  
|**XML Definition** page|Specify a definition for an XML document element or attribute.|  
|**Database Definition** page|Specify a definition for a database table or a database table column.|  
|**Specify the Display Name** page|Specify a format for displaying the vocabulary definition in rule conditions and actions.|  
|**Parameter Definition** window|Specify a parameter value for use in the display name for a vocabulary definition.|  
|**Fact Creator** list view|Browse through assemblies to add a reference to a .NET-based fact creator that provides short-term facts for testing a policy.|  
|**Fact Retriever** dialog box|Browse through assemblies to add a reference to a .NET-based fact retriever that provides long-term facts for policy execution.|  
|**Translator** dialog box|Browse through assemblies to add a reference to a .NET-based translator that translates a policy version into an executable representation for the rule set executor.|  
|**Output** window|View trace output from test execution of a selected policy version. Use the shortcut menu to save, clear, and import trace logs.|  
|**Test Policy** window|Select fact instances to use in testing a policy version.|  
  
## See Also  
 [Using Policy Explorer](../core/using-policy-explorer.md)   
 [Using Facts Explorer](../core/using-facts-explorer.md)   
 [Using Rule Editor](../core/using-rule-editor.md)   
 [Windows of the Business Rule Composer](../core/windows-of-the-business-rule-composer.md)