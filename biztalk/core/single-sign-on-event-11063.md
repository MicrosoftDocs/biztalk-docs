---
title: "Single Sign-On: Event 11063 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c84f91de-221d-43c4-8d23-3d1b7fd29cf7
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11063
## Details  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           11063                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N/A                             |
|  Symbolic Name  |          SSO_ERROR_PS_MIIS_CALLBACK_ACCESS_DENIED          |
|  Message Text   |      Password sync server (for MIIS) access denied.%r      |
  
## Explanation  
 MIIS Callback access has been denied. The most likely cause of this error is failure to use the Kerberos authentication between the ENTSSO system and MIIS.  
  
## User Action  
 Confirm that your ENTSSO system is using Kerberos authentication. For more information, see [SSO Security Recommendations](../core/sso-security-recommendations.md).