---
title: "SSO Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maps [SSO]"
  - "maps [SSO], creating"
  - "SSO, maps"
ms.assetid: b44f7a0c-595c-49dc-9d75-2e76f29dca88
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SSO Mappings
When an Enterprise Single Sign-On (SSO) administrator or an SSO affiliate administrator defines an affiliate application, the administrator can define it either as an application with individual mappings, or as an application with a group mapping.  
  
## Individual Mappings  
 SSO individual mappings enable administrators and users to create a one-to-one mapping between Windows users and their corresponding non-Windows credentials. When using individual mappings, users can manage their own mappings. The SSO system maintains the one-to-one relation for the user's Windows account and the user's non-Windows account.  
  
 Windows End-users can create and manage their own mappings for individual type applications. The same affiliate application can act as a Windows Initiated SSO and a Host Initiated SSO type application.  
  
> [!IMPORTANT]
>  Mappings can be created only for Windows domain accounts. Local accounts cannot be mapped.  
  
> [!NOTE]
>  Only individual users can obtain the credentials to their individual accounts when using individual mappings.  
  
## Group Mapping  
 SSO group mapping consists of mapping a Windows group, which contains multiple Windows users, to a single account in the affiliate application.  
  
 You can also specify multiple accounts for the SSO Application Users role. Each account you specify can be associated with an external account. For example, you can map a domain group account to EXTERNALUSER1 and an individual domain account to EXTERNALUSER2. If the same user has more than one mapping, the first mapping in the order of SSO Application Users is used.  
  
 Only an application administrator, SSO affiliate administrator, or SSO administrator can create or manage a group mapping.  
  
 You cannot specify the same group application for Windows initiated SSO and Host Initiated SSO.  
  
> [!IMPORTANT]
>  Mappings can be created only for Windows domain accounts. Local accounts cannot be mapped.  
  
> [!IMPORTANT]
>  When you use group mappings, the members of the group can obtain the credential information for the group mapping.  
  
## See Also  
 [Managing User Mappings](../core/managing-user-mappings.md)   
 [SSO Affiliate Applications](../core/sso-affiliate-applications.md)