---
title: "SSO System Properties: Options | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.esso.system.properties.options"
ms.assetid: d8df3e47-49e4-4acc-9b8e-7b4a2e5de21b
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
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
 [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)