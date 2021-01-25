---
description: "Learn more about: How to Develop Vocabularies"
title: "How to Develop Vocabularies | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, vocabularies"
  - "vocabularies, business rules"
  - "business rules, vocabularies"
  - "vocabularies, creating"
ms.assetid: 5c16eb98-2257-44f2-8a29-899e02f7e556
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Develop Vocabularies
Rule conditions and actions are based on sources that may have detailed, difficult-to-read binding information that tells the user little or nothing about what they refer to. The Business Rules Framework enables you to create vocabularies to simplify the development of rules by offering users intuitive, domain-specific terminology that users can associate with rule conditions and actions.  
  
 You can identify data sources to use, create a new vocabulary, and add vocabulary definitions to it. You can save a version of your vocabulary to the rule store, and when it is complete, you can publish it to provide users with a well-defined, immutable set of terms that are bound to data references.  
  
 If you need to make changes to your vocabulary in the future, you can simply create a new version of the vocabulary that reflects the changes.  
  
> [!CAUTION]
>  When a new version of a vocabulary is created, the rules built from a previous version will still point to the previous version.  
  
### To create a vocabulary  
  
1.  In the Facts Explorer window, click the **Vocabularies** tab.  
  
2.  Right-click the **Vocabularies** folder, and then click **Add New Vocabulary**.  
  
     A new **vocabulary** folder appears under the **Vocabularies** folder.  
  
3.  Click the new **vocabulary** folder, and then edit the name in the Properties window.  
  
    > [!NOTE]
    >  You must save everything (all versions of the definitions) before you can rename a vocabulary or a policy.
