---
title: "Configuring Enterprise Single Sign-On1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1d096a3-b456-454f-a45e-1c96bf2db94b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring Enterprise Single Sign-On
You can configure Enterprise Single Sign-On (SSO) using command-line utilities, user interface (UI) tools, or COM or Microsoft .NET Framework interfaces.  
  
## SSO Command-line Utilities  
 You use three different command-line utilities to perform Enterprise Single Sign-On tasks:  
  
 **SSOConfig.** Enables an SSO administrator to configure the Credential database and to manage the master secret.  
  
> [!NOTE]
>  The Configuration Wizard creates the Credential database and the master secret server.  
  
 **SSOManage.** Enables SSO administrators, SSO affiliate administrators, and application administrators to update the Credential database to add, delete, and manage applications, to administer user mappings, and to set credentials for the affiliate application users. Some operations can be performed only by the SSO administrators, or, only by the SSO administrators and SSO affiliate administrators.  
  
 **SSOClient.** Enables Single Sign-On users to manage their own user mappings and set their credentials.  
  
 For more information about the SSO accounts, see [Enterprise Single Sign-On User Groups](../esso/enterprise-single-sign-on-user-groups.md).  
  
## SSO UI Tools  
 **Enterprise SSO MMC Snap-in.** Enables SSO administrators, SSO affiliate administrators, and application administrators to update the SSO database, to add, delete, and manage applications, to administer user mappings, and to set credentials for the affiliate application users. Some operations can be performed only by the SSO administrators, or only by the SSO administrators and SSO affiliate administrators. All operations that can be performed by the application administrators can also be performed by the SSO administrators and SSO affiliate administrators.  
  
 **SSO Client Utility.** Enables end users to manage their own mappings and set their credentials using the UI tool.  
  
## SSO COM and .NET interfaces  
 Enterprise Single Sign-On provides COM and Microsoft .NET Framework programmatic interfaces that enable you to create custom components, and to create scripts to facilitate the administration of the SSO system.  
  
## See Also  
 [SSO Components](../esso/sso-components.md)   
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)   
 [Enterprise Single Sign-On Basics](../esso/enterprise-single-sign-on-basics.md)