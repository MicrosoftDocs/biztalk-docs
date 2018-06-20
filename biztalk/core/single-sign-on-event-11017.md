---
title: "Single Sign-On: Event 11017 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a4f7264-18aa-4eca-97c9-d5fd7e90e2cc
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11017
## Details  
  
|                 |                                                                                                                                                                                                                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                               Enterprise Single Sign-On                                                                                                                                |
| Product Version |                                                                                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                               |
|    Event ID     |                                                                                                                                         11017                                                                                                                                          |
|  Event Source   |                                                                                                                                         ENTSSO                                                                                                                                         |
|    Component    |                                                                                                                                          N/A                                                                                                                                           |
|  Symbolic Name  |                                                                                                                           SSO_PS_WARN_NOT_IN_GROUP_DELETE_OK                                                                                                                           |
|  Message Text   | The mapping is not valid because the Windows account is not in the Application Users account for the application. The mapping has been deleted.%r<br /><br /> Tracking ID: %1%r<br /><br /> Windows Account: %2%r<br /><br /> Application Name: %3%r<br /><br /> Application Users: %4 |
  
## Explanation  
 Either the Windows account specified was never a part of the Application Users account for this application, or it was at one time, but has been changed or removed. The mapping has been deleted.  
  
## User Action  
 Check the password sync account information for your system, and make sure your information is valid. Then recreate the mapping. Note that using the Create Mapping Wizard reduces the risk of invalid mapping information.