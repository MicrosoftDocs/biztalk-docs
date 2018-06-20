---
title: "Single Sign-On: Event 10566 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7bd140b-5503-40f8-bf5d-604fa763989e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10566
## Details  
  
|                 |                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                     Enterprise Single Sign-On                                                                      |
| Product Version |                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                     |
|    Event ID     |                                                                               10566                                                                                |
|  Event Source   |                                                                               ENTSSO                                                                               |
|    Component    |                                                                                N/A                                                                                 |
|  Symbolic Name  |                                                                  SSO_WARN_CANNOT_UPDATE_APP_FLAGS                                                                  |
|  Message Text   | You cannot update some of the specified flags for this application. They will be ignored.%r<br /><br /> Application Name: %1%r<br /><br /> Specified Flag Mask: %2 |
  
## Explanation  
 Certain flags in an application cannot be changed. (For example, it is not allowed to change an application type from Individual to Group.) The flags for this application are specified in the warning text.  
  
## User Action  
 No user action is required.