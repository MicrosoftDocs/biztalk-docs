---
title: "Enterprise Single Sign-On User Groups | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3267a756-3556-4a9c-af68-6cbe382059f9
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Enterprise Single Sign-On User Groups
To configure and manage the Enterprise Single Sign-On (SSO) system, you must create certain Windows groups and accounts for each of these roles. When configuring the access accounts in Enterprise SSO, you can specify more than one account for each of these roles. This section describes these roles.  
  
> [!IMPORTANT]
>  It is strongly recommended that you use domain groups when configuring SSO.  
  
> [!NOTE]
>  For security purposes, the SSO system does not allow for built-in accounts.  
  
## Single Sign-On Administrators  
 SSO administrators have the highest level user rights in the SSO system. They can do the following:  
  
- Create and manage the Credential database.  
  
- Create and manage the master secret.  
  
- Enable and disable the SSO system.  
  
- Create password synchronization adapters.  
  
- Enable and disable password synchronization in the SSO system.  
  
- Enable and disable host-initiated SSO.  
  
- Perform all administration tasks.  
  
  The SSO administrators account can be either a Windows group account or an individual account. The SSO administrators account can also be either a domain or local group or individual account. When you use an individual account, you cannot change it to another individual account. Therefore, it is recommended that you do not use an individual account. You can change this account to a group account as long as the original account is a member of the new group.  
  
> [!IMPORTANT]
>  The service account that runs the Enterprise Single Sign-On service must be a member of this group. To help secure your environment, ensure that no other service is using the same service account.  
  
## Single Sign-On Affiliate Administrators  
 The SSO affiliate administrator defines the affiliate applications that the SSO system contains. Affiliate applications are a logical entity that represents the back-end system to which you are connecting using SSO. SSO affiliate administrators can do the following:  
  
- Create and manage affiliate applications.  
  
- Specify the application administrators account for each affiliate application.  
  
- Perform all the administration tasks that the application administrators and application users can.  
  
  The SSO Affiliate Administrator account can be either a Windows group account or an individual account. The SSO Affiliate Administrator account can also be either a domain or local group or account.  
  
## Application Administrators  
 There is one application administrators group per affiliate application.  
  
 Members of this group can do the following:  
  
-   Change the application users group account.  
  
-   Create, delete, and manage credential mappings for all users of the specific affiliate application.  
  
-   Set credentials for any user in that specific affiliate application users group account.  
  
-   Perform all the administration tasks that the application users can.  
  
## Application Users  
 There is one application users group account for each affiliate application. This group contains the list of end users in an Enterprise SSO environment. Members of this group can do the following:  
  
-   Look up their credentials in the affiliate application.  
  
-   Manage their credential mappings in the affiliate application.  
  
> [!NOTE]
>  Remember to be vigilant when assigning groups. It is possible, for example, to use a Host Integration Server security user group for the SSO application users group. Before you do this, be certain that all users need all access that will then be available to them.  
  
## See Also  
 [How to Update the Properties of an Affiliate Application](../esso/how-to-update-the-properties-of-an-affiliate-application.md)   
 [How to Update the Credential Database](../esso/how-to-update-the-credential-database.md)   
 [Managing User Mappings](../esso/managing-user-mappings.md)   
 [Enterprise Single Sign-On Basics](../esso/enterprise-single-sign-on-basics.md)