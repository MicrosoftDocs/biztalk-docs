---
title: "Single Sign-On: Event 10601 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2624025e-b7a8-43b9-aa7e-6811a2fc3278
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10601
## Details  
  
|                 |                                                                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                  Enterprise Single Sign-On                                                                                                                   |
| Product Version |                                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                  |
|    Event ID     |                                                                                                                            10601                                                                                                                             |
|  Event Source   |                                                                                                                            ENTSSO                                                                                                                            |
|    Component    |                                                                                                                             N/A                                                                                                                              |
|  Symbolic Name  |                                                                                                                    SSO_WARN_INVALID_FLAGS                                                                                                                    |
|  Message Text   | The specified flags are not valid for creating this type of application.<br /><br /> See documentation for details.%r<br /><br /> Application Name: %1%r<br /><br /> Specified Flags: %2%r<br /><br /> Allowed Flags: %3%r<br /><br /> Not Allowed Flags: %4 |
  
## Explanation  
 The specified flags are not valid for creating this type of application. The warning lists the application concerned, as well as the flags that are allowed and those that are not.  
  
## User Action  
 Recreate the application following the guidelines outlined in the warning message.