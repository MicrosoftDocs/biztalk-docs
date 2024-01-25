---
description: "Learn more about: Single Sign-On: Event 10804"
title: "Single Sign-On: Event 10804"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10804
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10804                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N/A                             |
|  Symbolic Name  |                ENTSSO_E_INCORRECT_COMPUTER                 |
|  Message Text   |     This adapter is not configured for this computer.      |
  
## Explanation  
 Each adapter is configured to run on a specific computer, which is identified by its long name. Either the name is incorrect, or you are trying to run the adapter on a different computer.  
  
## User Action  
 See the configuration for this adapter to determine the proper name of the appropriate computer.
