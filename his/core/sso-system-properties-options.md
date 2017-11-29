---
title: "SSO System Properties: Options1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dd0e706-995e-424d-b1d3-f6e0d803cce3
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# SSO System Properties: Options
This screen displays options for the overall Enterprise Single Sign-On (SSO) system.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Allow tickets**|Determines whether tickets are allowed at the system level. Only an SSO Administrator can configure tickets at the SSO system level and at the Affiliate Application level.<br /><br /> If ticketing is disabled at the system level, it cannot be used at the Affiliate Application level either. It is possible to enable tickets at the system level and disable them at the Affiliate Application level.|  
|**Allow host initiated SSO**|By default, host initiated Single Sign-On is not enabled in the Single Sign-On system, and must be enabled by the SSO Administrator.|  
|**From Windows to adapters**|Determines whether Windows password changes (in Active Directory) will be sent to password sync adapters. Default is not selected.|  
|**From adapters to SSO database (partial sync)**|Determines whether external password changes received from password sync adapters will cause the password to be changed in the SSO database. Default is not selected.|  
|**From adapters to Windows (full sync)**|Determines whether external password changes received from password sync adapters will cause the Windows password to be changed in Active Directory. Default is not selected.|  
  
## See Also  
 [Enterprise Single Sign-On (Configuration)](../core/enterprise-single-sign-on-configuration.md)   
 [Enterprise Single Sign-On System](../core/enterprise-single-sign-on-system.md)