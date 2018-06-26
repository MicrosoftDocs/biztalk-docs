---
title: "Single Sign-On: Event 10524 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55e26da3-f67f-4f87-92e5-2f8765b19989
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10524
## Details  

|                 |                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                  Enterprise Single Sign-On                                                                                  |
| Product Version |                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                  |
|    Event ID     |                                                                                            10524                                                                                            |
|  Event Source   |                                                                                           ENTSSO                                                                                            |
|    Component    |                                                                                             N\A                                                                                             |
|  Symbolic Name  |                                                                               SSO_ERROR_RESTORE_SECRET_FAILED                                                                               |
|  Message Text   | Failed to restore the master secrets.%r<br /><br /> File Name: %1%r<br /><br /> Current MSID: %2%r<br /><br /> Previous MSID: %3%r<br /><br /> Client User: %4%r<br /><br /> Error Code: %5 |

## Explanation  
 This Error event indicates that a user attempt to restore the master secrets from a backup file failed. This might be due to permissions issues (you must be an SSO Administrator to restore the master secret) or possibly due to file corruption of the backup file. In these cases there should be related messages in the Application event log.  

## User Action  
 To resolve this error, do one or more of the following:  

- Check the Application event log for associated events or errors.  

- Check that you have the appropriate SSO Administrator permissions.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md)  

- [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md)  

- [How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md)
