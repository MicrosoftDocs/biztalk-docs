---
title: "SSO Support for Receive Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4767387c-f24b-4986-aaed-6724c5d6b347
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SSO Support for Receive Adapters
Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local, network, and domain boundaries. Transport adapter writers can leverage SSO APIs to handle the user credentials that a transport adapter uses to access back-end applications.  
  
 Transport adapters that do not support SSO are usually required to be configured with a single set of credentials that they use for accessing back-end applications. For many back-end systems, single account authentication may not satisfy all security enforcements. Many applications provide different access rights depending on the user who is accessing them. SSO allows adapters to dynamically choose the credentials to use for the endpoint based on the user who is trying to access it.  
  
## How Receive Adapters Work with SSO  
 Receive adapters that support SSO perform the following steps after receiving a message and before publishing it to BizTalk Server:  
  
1. The adapter impersonates the sender and obtains the SSO ticket on behalf of the sender by using the **ISSOTicket.IssueTicket** API.  
  
2. After successfully obtaining an SSO ticket the adapter stores it on the message context property “SSOTicket” under the system namespace.  
  
   The following code fragment demonstrates how the ticket is obtained and how it is stored on the message context.  
  
```  
public class MyAdapter : IBTTransport,   
                         IBTTransportConfig,   
                         IBTTransportControl,  
                         IPersistPropertyBag,   
                         IBaseComponent  
{  
...  
     private string m_SSOToken = null;  
  
 // Get a ticket for the sender  
     private void GetSSOTicket(IntPtr token)  
     {  
       bool impersonated = false;  
      WindowsImpersonationContext wic = null;  
  
 if (token != (IntPtr)0)   
 {  
     try   
 {  
         // Impersonate the user using his security  
 // token  
            WindowsIdentity wi =   
 new WindowsIdentity(token);  
            wic = wi.Impersonate();  
            impersonated = true;  
  
         // Get an SSO ticket for the impersonated  
 // user  
            ISSOTicket ssoTicket = new ISSOTicket();  
            m_SSOToken = ssoTicket.IssueTicket(0);  
         }  
         finally   
 {  
           if (impersonated)  
            // Revert the impersonation  
            wic.Undo();  
          }  
}  
}  
...  
  
     private void WriteSSOTicketToContext(  
 IBaseMessage message )  
     {  
         if (m_SSOTicket != null)   
 {  
 // Write the SSO ticket to the message context  
          message.Context.Write(  
 “SSOTicket”,  
 http://schemas.microsoft.com/BizTalk/2003/system-properties,   
 m_SSOToken);  
        }  
      }  
}  
```  
  
## Party Resolution  
 The Party Resolution pipeline component is responsible for mapping the sender certificate or the sender security identifier (SID) to the corresponding configured BizTalk Server party. Adapters that have this information available to them should set the two system message context properties, **WindowsUser** and **SignatureCertificate**, to be consumed by the downstream party resolution component if configured.  
  
 The **WindowsUser** property is populated with the domain user of the sender, for example redmond\myBtsUser. The **SignatureCertificate** property is populated with the thumbprint of the client authentication certificate.  
  
## Managing Passwords  
 If you put credentials directly in the properties of an endpoint, the password field will be blanked out when you need to export a binding file. This will require your user to re-enter the password as an administrator. You can avoid this difficulty by using SSO for credentials.  
  
 If the adapter endpoint has a **Password** property, be aware that the actual value is stored in clear text in the SSO Configure Store database. This is despite the fact that it is displayed in the user interface as "*". This property is also transferred through the network and a simple script using the BizTalk Server sample ExplorerOM will be able to read it.