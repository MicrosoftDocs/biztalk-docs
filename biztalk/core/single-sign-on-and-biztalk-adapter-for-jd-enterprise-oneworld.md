---
description: "Learn more about: Single Sign-On and BizTalk Adapter for JD Enterprise OneWorld"
title: "Single Sign-On and BizTalk Adapter for JD Enterprise OneWorld"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On and BizTalk Adapter for JD Enterprise OneWorld
Single Sign-On (SSO) credentials are obtained from the SSO credentials database; therefore, you do not need to enter the server system's logon credentials in the **Transport Properties** window.  
  
 At design-time, Microsoft BizTalk Adapter for JD Edwards OneWorld obtains the credentials for the system (for the specified affiliate application) under the context of the user who started BizTalk Server project. That user should be an Application User.  
  
 At run time, use the BizTalk Adapter for JD Edwards OneWorld as a receive location in the pass-through scenarios when using SSO.  
  
 When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user. The ISAPI extension impersonates the Windows user and calls the SSO credential store to obtain an encrypted ticket. This ticket is stored as the SSOTicket property in the context of the message.  
  
 The message is then directed to the Message Box database. When the adapter receives the message from the Message Box database, it calls the IBTSTicket.ValidateAndRedeemTicket method with the encrypted ticket along with the affiliate application name to retrieve the logon credentials from the SSO store. BizTalk Adapter for JD Edwards OneWorld then uses the external credentials to connect to the system and process the request.  
  
> [!NOTE]
>  SSO configuration is part of the BizTalk Server setup. If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, because this affects the function of the Enterprise SSO service. SSO only functions under a domain account.  
  
## See Also  
 [Creating Affiliate Applications](../core/creating-affiliate-applications3.md)   
 [Security in the adapter](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)
