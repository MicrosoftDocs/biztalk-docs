---
description: "Learn more about: Single Sign-On and BizTalk Adapter for PeopleSoft Enterprise"
title: "Single Sign-On and BizTalk Adapter for PeopleSoft Enterprise | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "processing HTTP requests"
  - "Single Sign-On, using with the adapter"
  - "HTTP requests, processing"
ms.assetid: d8ad75f1-a83f-4722-a43f-50dc95df2f9d
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On and BizTalk Adapter for PeopleSoft Enterprise
When you use Single Sign-On (SSO) with Microsoft BizTalk Adapter for PeopleSoft Enterprise, the adapter obtains the credentials from the SSO Credentials database; therefore, you do not have to enter the logon credentials for the server system in the **Transport Properties** dialog box.  
  
 At design-time, BizTalk Adapter for PeopleSoft Enterprise obtains the credentials for the system (for the specified affiliate application) under the context of the user who started the BizTalk Server project. That user should be an Application User.  
  
## Processing Requests  
 When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user. The ISAPI extension impersonates the Windows user and then calls the SSO credential store to obtain an encrypted ticket. This ticket is stored as the SSOTicket property in the context of the message.  
  
 The message is then directed to the Message Box database. When BizTalk Adapter for PeopleSoft Enterprises receives the message from the Message Box database, it calls ValidateAndRedeemTicket with the encrypted ticket together with the affiliate application name to retrieve the logon credentials from the SSO store. The adapter then uses the external credentials to connect to the system and process the request.  
  
> [!NOTE]
>  SSO configuration is part of the BizTalk Server setup. If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service. SSO only functions under a domain account.  
  
## See Also  
 [Creating Affiliate Applications](../core/creating-affiliate-applications2.md)   
 [Secure the adapter](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)
