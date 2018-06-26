---
title: "The Resolver Web Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 236cff15-562a-41d5-bfdc-d250186fb616
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Resolver Web Service
The Resolver Web service is a gateway into the ESB dynamic resolution mechanism. [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes two versions of this service: an ASP.NET (ASMX) version and a Windows Communication Foundation (WCF) version. The service names are **ESB.ResolverServices** and **ESB.ResolverServices.WCF**, respectively, and the services expose the following methods:  
  
- **Resolve.** This method takes as its single parameter a **String** that contains the resolver connection string for the request, which conforms to the standard connection strings for registered resolvers such as **STATIC, BRE, UDDI, XPATH, ITINERARY, ITINERARY-STATIC, BRI,** or **LDAP.**  
  
- **ResolveMessage.** This method takes as its first parameter a String that contains the resolver connection string for the request, which conforms to the standard connection strings for registered resolvers such as  **STATIC, BRE, UDDI, XPATH, ITINERARY, ITINERARY-STATIC, BRI,** or **LDAP**. In addition, the method accepts an optional second parameter as a **String** that contains an XML message document that the service can use as optional facts to assist in a resolution; for example, the BRE resolver may require a message body that encapsulates facts.  
  
  For more information about the Resolver and ResolverDictionary classes and their usage, see [Using the Helper Classes](../esb-toolkit/using-the-helper-classes.md).  
  
## Resolver Connection Strings  
 The ESB dynamic resolution mechanism uses a connection string preceded by a moniker that indicates the type of resolution to perform. The supported monikers include **STATIC, BRE, UDDI, UDDI3, XPATH, ITINERARY, ITINERARY-STATIC, BRI,** and **LDAP**. The following connection string shows an example of a **UDDI** moniker:  
  
```  
  
//UDDI  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=PurchaseOrder;serviceProvider=Microsoft.Practices.ESB  
```  
  
 For information about the types of connections strings supported by the dynamic resolution mechanism, see [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md).  
  
> [!NOTE]
>  You must configure this service to use either Windows Integrated Security and to run under the built-in NETWORK SERVICE account.  
>   
>  By default, the Resolver Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients. You should configure the service so that it requires SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and your BizTalk Server using network-level IPSec and appropriate file-level access control list (ACL) permissions. To avoid security risks, it is not recommended to expose this service outside the boundary of the trusted subsystem.