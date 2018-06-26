---
title: "Single Sign-On: Event 10748 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b4b18ea-6565-4c0b-89f8-30a8c67601ba
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10748
## Details  

|                 |                                                                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                              Enterprise Single Sign-On                                                                                              |
| Product Version |                                                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                              |
|    Event ID     |                                                                                                        10748                                                                                                        |
|  Event Source   |                                                                                                       ENTSSO                                                                                                        |
|    Component    |                                                                                                         N\A                                                                                                         |
|  Symbolic Name  |                                                                                           SSO_WARN_PS_ADAPTER_NOT_RUNNING                                                                                           |
|  Message Text   | Could not contact the destination adapter.<br /><br /> It may not be running or initialized.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> SSO Server Name: %3%r<br /><br /> Error Code: %4 |

## Explanation  
 This Warning event indicates that Password Synchronization could not contact the specified password sync adapter.  

## User Action  
 To resolve this warning, do one or more of the following:  

- Check the external adapter.  

- Use the MMC Snap-In or command line tools to enable the adapter.  

- Check the system and application event logs for associated errors.  

  For more information, see the following resources:  

- [How to Administer Password Synchronization](../core/how-to-administer-password-synchronization.md)
