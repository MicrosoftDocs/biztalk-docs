---
title: "Single Sign-On: Event 10522 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd634a57-01dc-44bd-bcf9-668689db7b77
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10522
## Details  

|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
|  Product Name   |                                   Enterprise Single Sign-On                                   |
| Product Version |                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                   |
|    Event ID     |                                             10522                                             |
|  Event Source   |                                            ENTSSO                                             |
|    Component    |                                              N\A                                              |
|  Symbolic Name  |                                      SSO_ERROR_REENCRYPT                                      |
|  Message Text   | SSO database re-encryption failed. Will try again in %1 minutes.%r<br /><br /> Error Code: %2 |

## Explanation  
 This Error event indicates that the SSO database re-encryption failed. When the SSO service starts on the master secret server, the first thing it does is to check if there is anything in the SSO database still encrypted with the previous master secret. If it finds anything, it decrypts that information (using the previous secret) and re-encrypts it using the current master secret. If for any reason this process fails, then this event message is issued.  

## User Action  
 To resolve this error, do the following:  

- Check the error code to determine what the underlying cause of the error might be. This could be a network or database issue. If it is intermittent, then no action is required because re-encryption will be attempted again after a short delay. If the issue is not intermittent, stop the SSO service and attempt to resolve the issue. Once the issue is resolved then restart the SSO service, Restarting the SSO service will automatically perform the re-encryption.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md)  

- [Master Secret Server](../core/master-secret-server.md)
