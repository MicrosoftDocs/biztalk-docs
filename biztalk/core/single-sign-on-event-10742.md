---
title: "Single Sign-On: Event 10742 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba62f878-ed12-421f-81ea-9285b2624fe9
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10742
## Details  

|                 |                                                                                                                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                         Enterprise Single Sign-On                                                                                                                                          |
| Product Version |                                                                                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                         |
|    Event ID     |                                                                                                                                                   10742                                                                                                                                                    |
|  Event Source   |                                                                                                                                                   ENTSSO                                                                                                                                                   |
|    Component    |                                                                                                                                                    N\A                                                                                                                                                     |
|  Symbolic Name  |                                                                                                                                         SSO_WARN_NO_UPDATE_ADAPTER                                                                                                                                         |
|  Message Text   | The client user must be a member of the SSO Administrators account or the Application Administrators account to update the adapter.%r<br /><br /> Client User: %1%r<br /><br /> SSO Administrators: %2%r<br /><br /> Application Administrators: %3%r<br /><br /> Adapter: %4%r<br /><br /> Error Code: %5 |

## Explanation  
 This Warning event indicates that an attempt to update the specified adapter was made, but could not be completed because the user account used is not a member of the SSO Administrators account or the Application Administrators account.  

## User Action  
 To resolve this warning, do one or more of the following:  

- Add user account to the SSO Administrators account or the Application Administrators account.  

- Retry update.  

  For more information, see the following resources:  

- [How to Administer Password Synchronization](../core/how-to-administer-password-synchronization.md)
