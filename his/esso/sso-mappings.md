---
title: "SSO Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d549ab36-3640-4891-aa65-7d09e972c440
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# SSO Mappings
When an Enterprise Single Sign-On (SSO) administrator or an SSO affiliate administrator defines an affiliate application, the administrator can define it either as an application that uses individual mappings, or as an application that uses a group mapping.  
  
## Individual Mappings  
 SSO individual mappings enable administrators and users to create a one-to-one mapping between Windows users and their corresponding non-Windows credentials. When individual mappings are used, users can manage their own mappings. The SSO system maintains the one-to-one relation for the user's Windows account and the user's non-Windows account.  
  
 Windows end users can create and manage their own mappings for individual type applications. The same affiliate application can act as a Windows-initiated SSO and a Host-initiated SSO type application.  
  
> [!IMPORTANT]
>  Mappings can be created only for Windows domain accounts. Local accounts cannot be mapped.  
  
> [!NOTE]
>  Only individual users can obtain the credentials to their individual accounts when individual mappings are used.  
  
## Group Mapping  
 SSO group mapping consists of mapping a Windows group, which contains multiple Windows users, to a single account in the affiliate application.  
  
 You can also specify multiple accounts for the SSO Application Users role. Each account that you specify can be associated with an external account.  
  
 For example, it is possible to map a domain user (domain\userA) to one set of external credentials (ExternalUser1). The same domain\userA could also be a member of Domain Group (domain\group1) and this group could be mapped to a different set of external credentials (ExternalUser2). In this case, it is important that the administrator (who must be an Application Administrator or above) specifies the correct order for the Application Users accounts.  
  
 The mapping for the first account (in the Order) of which the caller is a member is the one that will be used. In this case, if mapping for domain\userA to ExternalUser1 is set to Order 0, SSO will return this set of credentials for domain\UserA.  
  
 Only an application administrator, SSO affiliate administrator, or SSO administrator can create a group mapping.  
  
 You cannot specify the same group application for Windows-initiated SSO and Host-initiated SSO.  
  
> [!IMPORTANT]
>  Mappings can be created only for Windows domain accounts. Local accounts cannot be mapped.  
  
> [!IMPORTANT]
>  When you use group mappings, the members of the group can obtain the credential information for the group mapping.  
  
## See Also  
 [Managing User Mappings](../esso/managing-user-mappings.md)   
 [SSO Affiliate Applications](../esso/sso-affiliate-applications.md)   
 [Enterprise Single Sign-On Basics](../esso/enterprise-single-sign-on-basics.md)