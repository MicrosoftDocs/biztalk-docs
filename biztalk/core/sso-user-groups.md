---
title: "SSO User Groups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "administrator accounts, SSO"
  - "groups, SSO"
  - "user accounts, administrators"
  - "service accounts, SSO"
  - "SSO, user groups"
  - "SSO, service accounts"
  - "SSO, administrator accounts"
ms.assetid: e279001e-c724-4a2d-8939-0ba9dd08a19c
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SSO User Groups
To configure and manage the Enterprise Single Sign-On (SSO) system, you must create certain Windows groups and accounts for each of these roles. When configuring the access accounts in Enterprise SSO, you can specify more than one account for each of these roles. This section describes these roles.  
  
> [!IMPORTANT]
>  It is strongly recommended that you use domain groups when configuring SSO.  
  
> [!NOTE]
>  For security purposes, the SSO system does not allow built-in accounts.  
  
## Single Sign-On Administrators  
 SSO administrators have the highest level user rights in the SSO system. They can:  
  
- Create and manage the SSO database  
  
- Create and manage the master secret  
  
- Enable and disable the SSO system  
  
- Create password synchronization adapters  
  
- Enable and disable password synchronization in the SSO system  
  
- Enable and disable host initiated SSO  
  
- Perform all administration tasks  
  
  The SSO administrators account can be either a Windows group account or an individual account. The SSO administrators account can also be either a domain or local group or individual account. When using an individual account, you cannot change this account to another individual account. Therefore, it is recommended that you do not use an individual account. You can change this account to a group account as long as the original account is a member of the new account.  
  
> [!IMPORTANT]
>  The service account running the Enterprise Single Sign-On service must be a member of this account. To secure your environment, ensure that no other service is using the same service account.  
  
## Single Sign-On Affiliate Administrators  
 The SSO affiliate administrator defines the affiliate applications that the SSO system contains. Affiliate applications are a logical entity that represents the back-end system to which you are connecting using SSO. SSO affiliate administrators can:  
  
- Create, manage, and delete affiliate applications  
  
- Specify the application administrators account for each affiliate application  
  
- Perform all the administration tasks that the application administrators and application users can  
  
  The SSO Affiliate Administrator account can be either a Windows group account or an individual account. The SSO Affiliate Administrator account can also be either a domain or local group or account.  
  
## Application Administrators  
 There is one application administrators group per affiliate application.  
  
 Members of this group can:  
  
-   Change the application users group account  
  
-   Create, delete, and manage credential mappings for all users of the specific affiliate application  
  
-   Set credentials for any user in that specific affiliate application users group account  
  
-   Perform all the administration tasks that the application users can  
  
## Application Users  
 There is one application users group account for each affiliate application. This account contains the list of end users in an Enterprise Single Sign-On environment. Members of this account can:  
  
-   Look up their credentials in the affiliate application  
  
-   Manage their credential mappings in the affiliate application  
  
> [!NOTE]
>  Remember to be vigilant when assigning groups. It is possible, for example, to use a BizTalk Server security user group for the SSO application users group. Before you do this, be certain that all users need all access that will then be available to them.  
  
## See Also  
 [How to Update the Properties of an Affiliate Application](../core/how-to-update-the-properties-of-an-affiliate-application.md)   
 [How to Update the SSO Database](../core/how-to-update-the-sso-database.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)   
 [Understanding SSO](../core/understanding-sso.md)