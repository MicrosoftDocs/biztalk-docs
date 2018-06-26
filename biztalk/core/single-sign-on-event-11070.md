---
title: "Single Sign-On: Event 11070 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb669df9-710a-4792-bdd4-cca0c03fcda2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11070
## Details  
  
|                 |                                                                                                                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                               Enterprise Single Sign-On                                                                                               |
| Product Version |                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    Event ID     |                                                                                                         11070                                                                                                         |
|  Event Source   |                                                                                                        ENTSSO                                                                                                         |
|    Component    |                                                                                                          N/A                                                                                                          |
|  Symbolic Name  |                                                                                             SSO_WARN_PS_MIIS_NOT_ALLOWED                                                                                              |
|  Message Text   | This SSO server is currently not configured to allow Windows password changes from MIIS. Use 'ssoconfig -allowPS MIIS yes' or the SSO Administration MMC.%r<br /><br /> Tracking ID: %1%r<br /><br /> Client User: %2 |
  
## Explanation  
 This SSO server is currently not configured to allow Windows password changes from MIIS.  
  
## User Action  
 To allow Windows password changes from MIIS, in the **Servers Snap-In**, **Password Sync Properties** tab, select **Allow Password Sync from MIIS.**  
  
 For more information, see [How to Use the Servers Snap-in](../core/how-to-use-the-servers-snap-in.md).