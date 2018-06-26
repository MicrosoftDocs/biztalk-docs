---
title: "Select a URI scheme and addressing format when using the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bb4feee-3d39-43ca-82ac-aba38c13bc69
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Select a URI scheme and addressing format when using the WCF LOB Adapter SDK
A Uniform Resource Identifier (URI) uniquely identifies resources like a Web service or, in the case of an adapter developed with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], the system to connect to as well as the action to perform. This section provides a recommendation on how to construct a URI to uniquely describe the endpoint address and the action for your adapter.  
  
## Anatomy of a URI  
 A URI consists of the following three components:  
  
- **Scheme name** is the lead part of the URI string and is the first level of the naming structure; examples include http, urn, and contoso.  
  
- **Hierarchical part** consists of information that is usually hierarchical and can contain optional authority, hostname, and port information. Examples include www.microsoft.com and UserName=User@microsoft.com:4099.  
  
- **Query** contains optional information marked with a question mark (?) and typically grouped as key/value pairs separated by an ampersand (&). For example, contoso://microsoft.com/functions?name=Find.  
  
- **Fragment** is used to store extra identifying information that may be needed by the adapter. The fragment is separated by a hash (#); for example, contoso://microsoft.com/functions?name=Find#public.  
  
  You might not use all of the features provided by the URI syntax.  
  
## Designing the URI  
 As an adapter developer, you will have to devise an appropriate URI for your target line-of-business system. When designing your URI, it is important to make it unique and meaningful.  
  
 A unique URI is one that does not conflict with existing URIs within an organization and across other businesses and the Internet. For example, choosing a scheme name like "http" or "afs" that may be currently recognized or already in wide use could cause connection or operational problems because requests might be routed to a different system and not to your adapter.  
  
 Another important aspect of URI design is making it meaningful to the developer audience who will be consuming your adapter. For example, if you are writing an adapter for a medical claims processing system, you could design a URI scheme that includes your company name, the target claims processing system name, and system version: northwind.contoso.cps.v1.0://.  
  
## Connecting to the Target System  
 Connection strings have the following syntax:  
  
 **\<scheme\>://[userinfo "\@"]\<LOB Connection String\>**  
  
 For example, you could connect to the contoso catalog ordering system (a sample line of business application) using the following:  
  
 **northwind.contoso.v1.0://\<servername\>?Catalog=Contoso&Integrated Security=True**  
  
 You can also provide optional authority information in the URI including user name and password and other important credentials. However, this can present a security risk.  
  
> [!CAUTION]
>  Do not pass user credentials and other sensitive information in the URI. This information could be intercepted and viewed by unauthorized users.  
  
## See Also  
 [Plan and design an adapter using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)