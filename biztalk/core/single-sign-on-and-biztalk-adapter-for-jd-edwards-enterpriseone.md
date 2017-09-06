---
title: "Single Sign-On and BizTalk Adapter for JD Edwards EnterpriseOne | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JD Edwards EnterpriseOne adapters, Single Sign-On"
  - "Single Sign-On, JD Edwards EnterpriseOne adapters"
  - "adapters [JD Edwards EnterpriseOne adapters], Single Sign-On"
ms.assetid: efcc3a2d-18a6-4090-9e95-143fb7a356b2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On and BizTalk Adapter for JD Edwards EnterpriseOne
When you use Single Sign-On (SSO) with Microsoft   Adapter for JD Edwards EnterpriseOne, the adapter obtains the credentials from the SSO Credentials database. Therefore, you do not need to enter the logon credentials for the server system in the **Transport Properties** dialog box.  
  
 At design-time, BizTalk Adapter for JD Edwards EnterpriseOne obtains the credentials for the system (for the specified affiliate application) under the context of the user who started the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project. That user should be an Application User. At run time, use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Receive Adapter as a receive location in the pass-through scenarios when using SSO.  
  
## Processing Requests  
 When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user. The ISAPI extension impersonates the Windows user and calls the SSO credential store to obtain an encrypted ticket. This ticket is stored as the SSOTicket property in the context of the message.  
  
 The message is then directed to the Message Box database. When BizTalk Adapter for JD Edwards EnterpriseOne receives the message from the Message Box database, it calls `ValidateAndRedeemTicket` with the encrypted ticket along with the affiliate application name to retrieve the logon credentials from the SSO store. The adapter then uses the external credentials to connect to the system and process the request.  
  
> [!NOTE]
>  SSO configuration is part of the BizTalk Server setup. If you get SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service. SSO only functions under a domain account.  
  
## See Also  
 [Creating Affiliate Applications](../core/creating-affiliate-applications4.md)   
 [Using Single Sign-On](../core/using-single-sign-on1.md)