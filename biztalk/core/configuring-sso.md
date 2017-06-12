---
title: "Configuring SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSO, command line utilities"
  - "configuring, SSO"
  - "SSO, interfaces"
  - "SSOConfig [SSO]"
  - "SSO, configuring"
  - "SSOClient [SSO]"
  - "SSO, tools"
  - "SSOManage [SSO]"
ms.assetid: 6f755735-9b48-4771-beec-ced844f3d532
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring SSO
You can configure Enterprise Single Sign-On by using command line utilities, UI tools, or COM or Microsoft .NET interfaces.  
  
## SSO command line utilities  
 You use three different command line utilities to perform Enterprise Single Sign-On tasks:  
  
 **SSOConfig.** Enables an SSO administrator to configure the SSO database and to manage the master secret.  
  
> [!NOTE]
>  The Configuration Wizard creates the SSO database and the master secret server.  
  
 **SSOManage.** Enables SSO administrators, SSO affiliate administrators, and application administrators to update the SSO database to add, delete and manage applications, administer user mappings, and to set credentials for the affiliate application users. Some operations can be performed only by the SSO administrators, or, only by the SSO administrators and SSO affiliate administrators. All operations that can be performed by the Application Administrators can also be performed by the SSO Administrators and the SSO Affiliate Administrators.  
  
 **SSOClient.** Enables Single Sign-On users to manage their own user mappings and set their credentials.  
  
 For more information about the SSO accounts, see [SSO User Groups](../core/sso-user-groups.md).  
  
## SSO UI tools  
 **Enterprise SSO MMC Snap-in.** Enables SSO Administrators, SSO Affiliate Administrators, and Application Administrators to update the SSO database, to add, delete and manage applications, administer user mappings, and to set credentials for the affiliate application users. Some operations can be performed only by the SSO administrators, or only by the SSO administrators and SSO affiliate administrators. All operations that can be performed by the Application Administrators can also be performed by the SSO Administrators and SSO Affiliate Administrators.  
  
 **SSO Client Utility.** Enables end users to manage their own mappings and set their credentials using the UI tool.  
  
## SSO COM and .NET interfaces  
 Enterprise Single Sign-On provides COM and .NET programmatic interfaces that enable you to create custom components, and to create scripts to facilitate the administration of the SSO system.  
  
## See Also  
 [SSO Components](../core/sso-components.md)