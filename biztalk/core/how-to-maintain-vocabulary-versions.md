---
title: "How to Maintain Vocabulary Versions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, vocabularies"
  - "vocabularies, creating"
  - "vocabularies, versioning"
  - "vocabularies, publishing"
  - "versioning, vocabularies"
  - "updating, vocabularies"
  - "vocabularies, updating"
ms.assetid: 43593c6f-4590-4940-ac17-4015928e5838
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Maintain Vocabulary Versions
When you have added vocabulary definitions to a version of your vocabulary, you can save the version to the rule store for further development, or you can publish the version to create a well-defined, immutable set of data-bound terms that are available to users to add to rules as they develop their policies. Note that fact that existing rules will still point to the old versions.  
  
 This topic contains procedures for the following tasks:  
  
-   To save a vocabulary version  
  
-   To publish a vocabulary version  
  
-   To create an updated version of a vocabulary  
  
-   To create an empty new version of a vocabulary  
  
### To save a vocabulary version  
  
-   Right-click the version, and then click **Save**.  
  
### To publish a vocabulary version  
  
-   Right-click the version, and then click **Publish**.  
  
### To create an updated version of a vocabulary  
  
1.  Right-click an existing version, and then click **Copy**.  
  
2.  Right-click the vocabulary folder, and then click **Paste**.  
  
     A new version is created, with the same elements as the copied version.  
  
### To create an empty new version of a vocabulary  
  
-   Right-click the vocabulary folder, and then click **Add New Version**.  
  
    > [!NOTE]
    >  You can only use vocabulary definitions from published vocabularies.