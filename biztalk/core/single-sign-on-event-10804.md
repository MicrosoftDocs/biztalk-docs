---
title: "Single Sign-On: Event 10804 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4d98bef-fdc3-4627-bb5b-663fa502b965
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10804
## Details  
  
|                 |                                                            |
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