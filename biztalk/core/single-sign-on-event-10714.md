---
title: "Single Sign-On: Event 10714 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59d8509f-cc3e-40fa-ba3d-3dcb0e73c67a
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10714
## Details  

|                 |                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------|
|  Product Name   |                                     Enterprise Single Sign-On                                     |
| Product Version |                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                     |
|    Event ID     |                                               10714                                               |
|  Event Source   |                                              ENTSSO                                               |
|    Component    |                                                N\A                                                |
|  Symbolic Name  |                             SSO_WARN_PS_NOTIFICATION_RETRIES_EXPIRED                              |
|  Message Text   | Retries expired, discarding notification.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2 |

## Explanation  
 This Warning event indicates that the Password Sync notification retries have expired, and the notification has been discarded.  

 When a password change (from Windows to an external system) is delivered to a password sync adapter, the password sync adapter acknowledges that it has successfully processed the password change. If the password change does not occur within a specified amount of time, or if another problem occurs during the change, the password change is delivered to the password sync adapter again. This is done a limited number of times (max retries) and then the password change notification is discarded.  

## User Action  
 To resolve this warning, do the following:  

- Check System and Application event logs for associated events.  

  For more information, see the following resources:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
