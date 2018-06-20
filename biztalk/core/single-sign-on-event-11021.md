---
title: "Single Sign-On: Event 11021 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70b987aa-8097-4243-a25b-f1cc12c5bc6a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11021
## Details  
  
|                 |                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                          Enterprise Single Sign-On                                                                                                                                                                          |
| Product Version |                                                                                                                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                          |
|    Event ID     |                                                                                                                                                                                    11021                                                                                                                                                                                    |
|  Event Source   |                                                                                                                                                                                   ENTSSO                                                                                                                                                                                    |
|    Component    |                                                                                                                                                                                     N/A                                                                                                                                                                                     |
|  Symbolic Name  |                                                                                                                                                           SSO_INFO_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_ALLOWED                                                                                                                                                            |
|  Message Text   | An external password change will cause a different external account to be changed.%r<br /><br /> This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Windows Account: %3%r<br /><br /> External Account 1: %4%r<br /><br /> External Account 2: %5 |
  
## Explanation  
 This is an informational message stating that an external password change will cause a different external account to be changed.  
  
## User Action  
 You should confirm immediately that this change was made with your knowledge and authorization. If so, no action is required. If not, find out where the change initiated, and confirm that it was a location safely within the system.