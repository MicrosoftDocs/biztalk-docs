---
title: "Translator Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.bre.translator"
helpviewer_keywords: 
  - "Translator dialog box [Business Rule Composer]"
  - "Business Rule Composer, Translator dialog box"
ms.assetid: 2470adb5-b6b8-40b2-b6f4-dc72579ef389
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Translator Dialog Box
Use the **Translator** dialog box to browse through assemblies to add a reference to a .NET-based translator that translates a policy version into an executable representation for the rule set executor.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Browse**|Browse through assemblies that implement rule set translators.|  
|**Assembly**|From the drop-down list, select the .NET assembly that contains the currently configured translator, or select **(None)** to clear the configuration.|  
|**Class**|From the drop-down list, select a public .NET class that implements the **IRuleSetTranslator** interface.|  
  
## See Also  
 [How to Create Vocabulary Definitions](../core/how-to-create-vocabulary-definitions.md)   
 [Windows of the Business Rule Composer](../core/windows-of-the-business-rule-composer.md)