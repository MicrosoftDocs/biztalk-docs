---
title: "Single Sign-On: Event 10850 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04e2af52-d35b-491a-a983-d80442dd6aef
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10850
## Details  
  
|                 |                                                                     |
|-----------------|---------------------------------------------------------------------|
|  Product Name   |                      Enterprise Single Sign-On                      |
| Product Version |     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]      |
|    Event ID     |                                10850                                |
|  Event Source   |                               ENTSSO                                |
|    Component    |                                 N/A                                 |
|  Symbolic Name  |                 ENTSSO_E_ENABLED_NOT_ALLOWED_CREATE                 |
|  Message Text   | An application cannot be created with the 'enabled' flag specified. |
  
## Explanation  
 Before enabling an application, it is necessary to both create the application and enter the field information for each of its fields (i.e. UserID and Password). It is not possible to create an application with the “enabled” field already set.  
  
## User Action  
 Create the application again (using either the Create Application API or the Create New Affiliate Application Wizard). When the application is complete and the fields populated, enable the application.