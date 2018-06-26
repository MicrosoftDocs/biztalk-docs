---
title: "How Host Integration Server Uses Active Directory2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14ac22b7-9636-4e25-a15c-5150b222460c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How Host Integration Server Uses Active Directory
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] uses Active Directory by registering services and resources with the Active Directory schema. The benefits of using Active Directory include:  
  
- Client configuration and resource location on the network is simplified.  
  
- The limitation of 8,000 sponsor connections that existed in SNA Server 4.0 is eliminated.  
  
  Host Integration Server client computers must be configured to communicate to a Host Integration Server computer using either sponsor connections or Active Directory. A client computer cannot be set up to use both at the same time.  
  
  If a Host Integration Server computer is configured to use Active Directory, it must operate in an Organizational Unit (OU). If this is the first Host Integration Server to be configured to use Active Directory, then you must perform the following steps:  
  
1. Create an OU for the Host Integration Server if one does not already exist.  
  
2. Grant Read/Write access to the OU service account used for the Host Integration Server.  
  
3. Grant Read access to the desktop users configured to use Active Directory for resource location.  
  
4. The Active Directory schema must be extended to include the Host Integration Server schema.  
  
   In addition, the following relationships between the SNA subdomain and the OU containing the Host Integration Server-specific containers must be observed:  
  
-   Multiple Host Integration Server computers can exist within the same OU.  
  
-   Each OU containing a Host Integration Server must be a unique SNA subdomain.  
  
-   Two different SNA subdomains cannot exist within the same OU.  
  
-   An SNA subdomain cannot stretch across two OUs.  
  
-   If an OU contains multiple Host Integration Server computers, they must be part of the same SNA subdomain.  
  
-   The name of the OU and the name of the SNA subdomain within that OU can either be the same name or different names.  
  
## See Also  
 [Active Directory Services](../core/active-directory-services2.md)   
 [How to Configure Active Directory During Host Integration Server Installation](../core/how-to-configure-active-directory-during-host-integration-server-installation1.md)   
 [Active Directory Administration](../core/active-directory-administration2.md)