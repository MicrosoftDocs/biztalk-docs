---
title: "Single Sign-On: Event 10526 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f72d466-8b63-453c-b608-f9d64f635f65
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10526
## Details  

|                 |                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                     Enterprise Single Sign-On                                                                     |
| Product Version |                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                     |
|    Event ID     |                                                                               10526                                                                               |
|  Event Source   |                                                                              ENTSSO                                                                               |
|    Component    |                                                                                N\A                                                                                |
|  Symbolic Name  |                                                                 SSO_ERROR_GENERATE_SECRET_FAILED                                                                  |
|  Message Text   | Failed to generate a new master secret.%r<br /><br /> Client User: %1%r<br /><br /> Client Computer:%2%r<br /><br /> Tracking ID: %3%r<br /><br /> Error Code: %4 |

## Explanation  
 This Error event indicates that a user attempt to generate a new master secret has failed. This might be due to permissions issues (you must be an SSO Administrator to generate the master secret) or possibly there were problems writing the master secret to the backup file. In these cases there should be related messages in the Application event log.  

## User Action  
 To resolve this error, do one or more of the following:  

- Check the Application event log for associated events or errors.  

- Check that you have the appropriate SSO Administrator permissions.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md)  

- [Managing the Master Secret](../core/managing-the-master-secret.md)
