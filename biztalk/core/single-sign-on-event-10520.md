---
title: "Single Sign-On: Event 10520 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91662072-d87c-4290-8afb-2143143ee858
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10520
## Details  

|                 |                                                                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                       Enterprise Single Sign-On                                                        |
| Product Version |                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                       |
|    Event ID     |                                                                 10520                                                                  |
|  Event Source   |                                                                 ENTSSO                                                                 |
|    Component    |                                                                  N\A                                                                   |
|  Symbolic Name  |                                                          SSO_WARN_NO_SECRETS                                                           |
|  Message Text   | No secrets were found in the registry of the master secret server. Use the configuration tools to generate or restore a master secret. |

## Explanation  
 This Warning event indicates that no secrets were found in the registry of the master secret server. The SSO master secrets are stored encrypted in the registry of the SSO master secret server. Two secrets are typically kept in the registry: the current master secret, and the previous master secret. Secrets are identified using a GUID (the master secret id). If the specified master secret cannot be found in the registry when requested, this error code will be returned.  

## User Action  
 To resolve this warnming, do one or more of the following:  

- Check that the master secret server name is correct and as expected.  

- If it is correct, check that the master secret is present in the registry of that master secret server. The master secret is located under HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS (this key is present only on the SSO master secret server).  

- If that key is missing then the master secret is not present. There should be one or more keys under SSOSS named as GUIDs which contain the encrypted keys. If these are not present then the master secret is not present. Master secrets are identified with GUIDs (the master secret id) so these GUIDs (if present) should match the master secret id of the secret that was requested. If there are keys named as GUIDs but they don’t match the requested master secret id, then there is a mixup between the master secret in the registry and the secret that was used to encrypt the data in the SSO database (SSODB). It may be necessary to restore a different master secret in this case, or maybe the SSODB has been restored from a downlevel backup. If the master secret is not present at all, then it can be restored form backup using the SSO configuration tools (command line or MMC) or a new secret can be generated. Note that you would normally only want to generate a new master secret if this is a new installation and there is no existing encrypted data in the SSO database. The master secret is normally generated for the first time during initial configuration.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [Master Secret Server](../core/master-secret-server.md)  

- [Managing the Master Secret](../core/managing-the-master-secret.md)  

- [Configuring SSO](../core/configuring-sso.md)
