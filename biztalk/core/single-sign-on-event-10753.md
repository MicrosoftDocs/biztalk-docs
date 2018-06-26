---
title: "Single Sign-On: Event 10753 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b538083-180b-4a15-bedf-aac4fc351c30
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10753
## Details  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10753                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N/A                             |
|  Symbolic Name  |                  ENTSSO_E_MAPPING_EXISTS                   |
|  Message Text   |                The mapping already exists.                 |
  
## Explanation  
 This mapping already exists, either on the Windows account already in use or the external account.  
  
## User Action  
 Check the existing mappings and the mapping you are trying to create. If the mapping you want already exists, use it and delete your new one. If not, delete your new one and recreate it.