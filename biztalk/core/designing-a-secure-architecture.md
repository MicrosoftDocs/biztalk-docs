---
description: "Learn more about: Designing a Secure Architecture"
title: "Designing a Secure Architecture"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Designing a Secure Architecture
For complete information about the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 The architecture presented in the topic [Large Distributed Architecture](../core/large-distributed-architecture.md) addresses many of the potential security threats to which a BizTalk environment is vulnerable. However, you need to evaluate your business assets, the threats that are a concern for your business, and the resources you have available to protect your assets and mitigate your potential threats to determine what the best architecture is for you. This section provides additional security options you can consider when designing your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architecture.  
  
## Firewalls  
 You can use physical (hardware) or software firewalls to restrict access to the resources in your environment. While the topic [Large Distributed Architecture](../core/large-distributed-architecture.md) uses Forefront Threat Management Gateway (TMG) 2010 server, you can create a similar architecture by using hardware or third-party software firewalls, as long as you open and configure the ports required for communication between the different BizTalk Server components. For more information about the ports BizTalk Server uses, see [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md).  
  
## Active Directory  
 In the sample deployment, Active Directory® directory service is used to create a hard security boundary around each group of servers. With the one-way trusts, you can further protect the BizTalk Server environment from attacks due to flaws in other non-BizTalk Server applications running on the processing servers, as the BizTalk Server applications run under accounts created in the data domain. Because the data domain does not trust any accounts in any other domain, a compromise of an account in another domain keeps the BizTalk Server environment from being compromised.  
  
## IPSec and SSL  
 If your environment does not pose critical threats that require the level of security firewalls provide, but the network segments that connect the data, processing, and services domains are not physically secure from various network attacks (for example packet sniffing or tampering), you still need to protect the data as it goes from one server to another. In this case, you can use Internet Protocol security (IPSec) or Secure Sockets Layer (SSL) to encrypt traffic from one server to another.  
  
## See Also  
 [Designing a Distributed Architecture](../core/designing-a-distributed-architecture.md)   
 [Planning for Security](../core/planning-for-security.md)   
 [Designing the System Architectures for BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md)
