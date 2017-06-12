---
title: "Logon Credentials Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.hostinstance.properties.general.logon"
ms.assetid: 3a96bd80-3959-456c-b3a3-aa3ffc1a9857
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Logon Credentials Dialog Box
Use the **Logon Credentials** dialog box to supply the account name and password of the SQL account under which the host instance will run. When you set up this account, BizTalk Server adds the account to the "Log on as a service" security policy.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Logon**|Type the domain and account name of the SQL account under which the host instance will run. The account name specified must be a member of the BizTalk Server Host Windows group.|  
|**Password**|Type the password that the host instance SQL account will use to authenticate the host instance on the BizTalk server.|  
  
## See Also  
 [Host Instances](../core/host-instances.md)   
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [How to Update the SSO Database](../core/how-to-update-the-sso-database.md)