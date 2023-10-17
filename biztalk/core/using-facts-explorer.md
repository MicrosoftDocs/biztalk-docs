---
description: "Learn more about: Using Facts Explorer"
title: "Using Facts Explorer | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Business Rule Composer, Facts Explorer"
  - "business rules, vocabularies"
  - "business rules, schemas"
  - "business rules, databases"
  - "business rules, .NET classes"
  - "Facts Explorer [Business Rule Composer]"
ms.assetid: ee125eb1-d5b9-4121-8a25-fcb7a640570e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Facts Explorer
The Facts Explorer contains four tabs: **Vocabularies**, **XML Schemas**, **Databases**, and **.NET Classes**.  
  
## Vocabularies tab  
 Use the **Vocabularies** tab in the Facts Explorer to manage vocabulary versions and definitions.  
  
 Use the shortcut menu to access the following options.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Add New Vocabulary**|Create a new vocabulary.|  
|**Add New Version**|Create a new empty version of the selected vocabulary. You can copy definitions from other versions and paste them into the new version.|  
|**Paste Vocabulary Version**|Paste the contents of a previously copied vocabulary version as a new version in the selected vocabulary.|  
|**Delete**|Delete the selected vocabulary and all its versions.|  
|**Add New Definition**|Launch the Vocabulary Definition Wizard to create a new definition in the selected vocabulary version.|  
|**Save**|Save the changes made to the selected version and its definitions.|  
|**Publish**|Publish the selected vocabulary version. Note that you cannot directly modify a published version. You can copy and paste it to a new version of the vocabulary.|  
|**Reload**|Reload the selected vocabulary version and its definitions, with the option to discard any current changes made in that version and restore the contents from the rule store.|  
|**Modify**|Launch the Vocabulary Definition Wizard to change the selected definition. Note that you cannot modify a definition that is part of a published vocabulary version.|  
|**Go to source fact**|For the selected definition, go to the corresponding source fact in a .NET assembly, XML schema, or database table.|  
  
## XML Schemas tab  
 Browse through XSD schemas for the definitions of XML elements and attributes. You can drag items onto unpublished vocabulary versions on the **Vocabulary** tab to create definitions, or you can drag items to the Conditions Editor or Actions Editor to define predicates, actions, and arguments.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Select Root Node**|Select a root node to load from an XML schema that contains multiple root notes.|  
  
## Databases tab  
 Browse through database servers for databases and table definitions. You can drag items onto unpublished vocabulary versions on the **Vocabulary** tab to create definitions, or you can drag items to the Conditions Editor or Actions Editor to define predicates, actions, and arguments.  
  
## .NET Classes tab  
 Browse through .NET assemblies for public .NET class definitions. You can drag items onto unpublished vocabulary versions on the **Vocabulary** tab to create definitions, or you can drag items to the Conditions Editor or Actions Editor to define predicates, actions, and arguments.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Browse**|Load a .NET assembly from the global assembly cache|  
|**Remove**|Remove a .NET assembly|
