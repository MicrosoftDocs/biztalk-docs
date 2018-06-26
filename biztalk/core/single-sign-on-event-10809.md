---
title: "Single Sign-On: Event 10809 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7331d12b-1000-4a60-83b3-f092968e0e51
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10809
## Details  
  
|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
|  Product Name   |                     Enterprise Single Sign-On                     |
| Product Version |    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]     |
|    Event ID     |                               10809                               |
|  Event Source   |                              ENTSSO                               |
|    Component    |                                N/A                                |
|  Symbolic Name  |                  ENTSSO_E_HISSO_APP_NOT_ENABLED                   |
|  Message Text   | The application is not enabled for Host Initiated Single Sign-On. |
  
## Explanation  
 The application is not enabled for Host Initiated Single Sign-On.  
  
## User Action  
 Use the administrative tools to configure Host Initiated Single Sign-On. This will set the  
  
 SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS flag on the application.