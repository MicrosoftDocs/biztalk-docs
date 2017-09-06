---
title: "SSO Support for Send Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45dc2597-0036-4444-8b35-d18621b003d8
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SSO Support for Send Adapters
Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local, network, and domain boundaries. When you create a transport adapter, you can leverage SSO APIs to handle the user credentials that a transport adapter uses to access back-end applications.  
  
 Transport adapters that do not support SSO are usually required to be configured with a single set of credentials that they use for accessing back-end applications. For many back-end systems, single account authentication may not satisfy all security enforcements. Many applications provide different access rights depending on the user who is accessing them. SSO allows adapters to dynamically choose the credentials to use for the endpoint based on the user who is trying to access it.  
  
## How Send Adapters Work with SSO  
 Send adapters that support SSO validate and redeem the ticket and obtain the user credentials from the SSO system by using the **ISSOTicket.ValidateAndRedeemTicket** API. The adapter uses the obtained credentials to authenticate with the destination endpoint.  
  
 The following code fragment demonstrates how a send adapter obtains the user credentials from the SSO system:  
  
```  
public class MyAdapter : IBTTransport,   
                         IBTTransportConfig,   
                         IBTTransportControl,  
                        IPersistPropertyBag,   
                         IBaseComponent  
{  
...  
     private string m_UserName = null;  
     private string m_UserPassword = null;  
  
 // Get user credentials from SSO  
 // AffiliateAppVal is the name of SSO affiliate   
 // application for the specific destination endpoint  
     private void GetUserCredentials(  
 IBaseMessage message,   
 string AffiliateAppVal )  
     {  
 string creds[] = null;  
 string externalUserName = null;  
  
 ISSOTicket ssoTicket = new ISSOTicket();  
 creds = ssoTicket.ValidateAndRedeemTicket(  
 message,   
 AffiliateAppVal,   
 0,   
 out externalUserName);  
  
 m_UserName = externalUserName;  
 m_UserPassword = creds[0];  
     }  
...  
}  
```  
  
## Party Resolution  
 The Party Resolution pipeline component is responsible for mapping the sender certificate or the sender security identifier (SID) to the corresponding configured BizTalk Server party. Adapters that have this information available to them should set the two system message context properties, **WindowsUser** and **SignatureCertificate**, to be consumed by the downstream party resolution component if configured.  
  
 The **WindowsUser** property is populated with the domain user of the sender, for example redmond\myBtsUser. The **SignatureCertificate** property is populated with the thumbprint of the client authentication certificate.  
  
## Managing passwords  
 If you put credentials directly in the properties of an endpoint, the password field will be blanked out when you need to export a binding file. This will require your user to re-enter the password as an administrator. You can avoid this difficulty by using SSO for credentials.