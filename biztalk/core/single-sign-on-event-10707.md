---
title: "Single Sign-On: Event 10707 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59629786-4f98-4861-aba3-153670bafc12
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10707
## Details  

|                 |                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                       Enterprise Single Sign-On                                                                        |
| Product Version |                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                       |
|    Event ID     |                                                                                 10707                                                                                  |
|  Event Source   |                                                                                 ENTSSO                                                                                 |
|    Component    |                                                                                  N\A                                                                                   |
|  Symbolic Name  |                                                                        SSO_WARN_PS_NO_APP_SYNC                                                                         |
|  Message Text   | Password sync flags for this adapter must allow password sync and must match the global flags. Check the adapter flags and the global flags.%r<br /><br /> Adapter: %1 |

## Explanation  
 This Warning event indicates that password sync flags for this adapter must allow password sync and must match the global flags.  

 Password sync for a password sync adapter is controlled by two flags, one allows sending of password to external systems (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL) and another which allows receiving of passwords from external systems (SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB). For successfull password sync these must be set for both the “global flags” and also for the specific adapter flags. This warning event is issued when password sync is requested by an external password sync adapter and neither of these flags is set for both the “global flags” and the adapter flags.  

## User Action  
 To resolve this warning, do the following:  

-   Use the SSO Admin MMC Snap-In (System &#124; Properties &#124; Options) or command line tool  `ssomanage –enable winsync/extsync` to enable the global flags.  

## More info

- **Enterprise Single Sign-On Flags** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  

- [How to Administer Password Synchronization](../core/how-to-administer-password-synchronization.md)
