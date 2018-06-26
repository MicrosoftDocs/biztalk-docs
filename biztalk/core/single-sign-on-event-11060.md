---
title: "Single Sign-On: Event 11060 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4851fba-0d3a-4a29-b720-a1d175d20555
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11060
## Details  
  
|                 |                                                                                                                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                               Enterprise Single Sign-On                                                                                               |
| Product Version |                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    Event ID     |                                                                                                         11060                                                                                                         |
|  Event Source   |                                                                                                        ENTSSO                                                                                                         |
|    Component    |                                                                                                          N/A                                                                                                          |
|  Symbolic Name  |                                                                                            SSO_WARN_PS_MIIS_ACCESS_DENIED                                                                                             |
|  Message Text   | Windows password changes from MIIS will only be accepted from the SSO service account.%r<br /><br /> Tracking ID: %1%r<br /><br /> Client User: %2%r<br /><br /> SSO Service Account: %3%r<br /><br /> Error Code: %4 |
  
## Explanation  
 A password change has been received by the ENTSSO server from Microsoft Identity Integration Server (MIIS). However, the ENTSSO server will only accept password changes from MIIS if the Client User (the caller) is the same account as the SSO service account.  
  
## User Action  
 Check the configuration of the caller for password sync in MIIS. For more information, see [How to Configure ENTSSO for MIIS Password Sync](../core/how-to-configure-entsso-for-miis-password-sync.md).