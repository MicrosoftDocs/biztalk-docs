---
description: "Learn more about: Single Sign-On: Event 10753"
title: "Single Sign-On: Event 10753"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10753
## Details  
  
| Field | Error Details |
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
