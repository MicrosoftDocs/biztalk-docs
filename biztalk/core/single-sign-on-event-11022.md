---
title: "Single Sign-On: Event 11022 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c65ca12b-dda8-408b-9512-39df6f8e035b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11022
## Details  
  
|                 |                                                                                                                                                                                                                                                                                                                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                                                                   Enterprise Single Sign-On                                                                                                                                                                                    |
| Product Version |                                                                                                                                                                   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                                                                   |
|    Event ID     |                                                                                                                                                                                             11022                                                                                                                                                                                              |
|  Event Source   |                                                                                                                                                                                             ENTSSO                                                                                                                                                                                             |
|    Component    |                                                                                                                                                                                              N/A                                                                                                                                                                                               |
|  Symbolic Name  |                                                                                                                                                                   SSO_WARN_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED                                                                                                                                                                   |
|  Message Text   | An external password change would have caused a different external account to be changed.%r<br /><br /> This has been prevented because the adapter for this external system is configured to not allow mapping conflicts.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Windows Account: %3%r<br /><br /> External Account 1: %4%r<br /><br /> External Account 2: %5 |
  
## Explanation  
 This is an informational message reporting the failure of an external password change which would have caused a different external account to be changed.  
  
## User Action  
 Although no change was made (because this system is configured to not allow mapping conflicts) you should confirm immediately that this attempt was made with your knowledge and authorization. If so, no action is required. If not, find out where the change initiated, and confirm that it was a location safely within the system.