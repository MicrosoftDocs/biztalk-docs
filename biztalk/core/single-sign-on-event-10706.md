---
title: "Single Sign-On: Event 10706 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d73db77e-5bb6-431c-a8ca-5682d7ab3d6a
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10706
## Details  

|                 |                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                 Enterprise Single Sign-On                                                 |
| Product Version |                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                 |
|    Event ID     |                                                           10706                                                           |
|  Event Source   |                                                          ENTSSO                                                           |
|    Component    |                                                            N\A                                                            |
|  Symbolic Name  |                                                SSO_WARN_PS_NO_GLOBAL_SYNC                                                 |
|  Message Text   | Group adapters require password sync to be allowed by the global flags. Check the global flags.%r<br /><br /> Adapter: %1 |

## Explanation  
 This Warning event indicates that password sync is requested by an external password sync adapter and neither of the global flags is set. There are two flags, one that allows sending of password to external system: SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL and another that allows receiving of passwords from external systems SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB.  

## User Action  
 To resolve this warning, do the following:  

-   Use the SSO Admin MMC Snap-In, (System &#124; Properties &#124; Options) or command line tool  `ssomanage –enable winsync/extsync` to enable the global flags.  

## More info

- **Enterprise Single Sign-On Flags** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

- [How to Administer Password Synchronization](../core/how-to-administer-password-synchronization.md)
