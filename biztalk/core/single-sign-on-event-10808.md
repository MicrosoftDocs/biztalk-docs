---
description: "Learn more about: Single Sign-On: Event 10808"
title: "Single Sign-On: Event 10808"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10808
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------|
|  Product Name   |                    Enterprise Single Sign-On                     |
| Product Version |    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]    |
|    Event ID     |                              10808                               |
|  Event Source   |                              ENTSSO                              |
|    Component    |                               N/A                                |
|  Symbolic Name  |                ENTSSO_E_HISSO_SYSTEM_NOT_ENABLED                 |
|  Message Text   | The SSO system is not enabled for Host Initiated Single Sign-On. |
  
## Explanation  
 The SSO system is not enabled for Host Initiated Single Sign-On.  
  
## User Action  
 Use the administrative tools to configure Host Initiated Single Sign-On. This will set the  
  
 SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS flag on the global information.
