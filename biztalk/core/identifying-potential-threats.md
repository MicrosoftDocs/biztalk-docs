---
title: "Identifying Potential Threats | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "planning, security"
  - "security, potential threats"
  - "security, planning"
ms.assetid: 1d70a0c1-6daf-47bb-af15-a4b35a7bafc2
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Identifying Potential Threats
You can use the STRIDE model to identify potential threats to your BizTalk Server deployment. STRIDE is an acronym derived from the following categories: *S*poofing identity, *T*ampering with data, *R*epudiation, *I*nformation disclosure, *D*enial of service, and Elevation of privileges. This section contains examples of potential threats to a BizTalk Server environment, and mechanisms to mitigate them.  
  
 **Spoofing identity**  
  
- If you save passwords in the binding files, and save these binding files, unauthorized users could read the passwords and use them to connect to the BizTalk Servers, and possibly cause harm. You should not save passwords in binding files, and you should use discretionary access control lists (DACLs) to restrict access to files that may contain sensitive data.  
  
  **Tampering with data**  
  
- Malicious users can intercept messages from partners to BizTalk Server, and modify the content of the message. You can use digital signatures to prevent malicious users from tampering with messages while they are in transit.  
  
  **Repudiation**  
  
- You need to keep track of messages that BizTalk sends and receives. You can use digital signatures to prove that you sent a message and that your partners sent you a message.  
  
  **Information disclosure**  
  
- Malicious users can read clear-text communication between BizTalk Server and Microsoft SQL Server™. You can use Internet Protocol security (IPSec), or Secure Sockets Layer (SSL) to help secure the communication between servers. You can use firewalls to limit access to each server. You can use encryption to help ensure the privacy of the message while it is in transit.  
  
- Unauthorized users may access information on network shares or directories. You can use strong discretionary access control lists (DACLs) to limit access to the accounts that use the resources.  
  
- The Windows administrator on a computer running a BizTalk Host instance can misbehave and carry out different levels of attacks (for example, information disclosure, or denial of service). However, in most cases you can limit these attacks to the particular host whose computer the attacker compromised.  
  
  **Denial of service**  
  
- A malicious user can send a large number of messages to BizTalk Server, which could prevent BizTalk from receiving valid messages. For more information about mitigation techniques to this threat, see [Mitigating Denial of Service Attacks](../core/mitigating-denial-of-service-attacks.md).  
  
  **Elevation of privileges**  
  
- Elevation of privileges threats typically occur when code you do not trust runs in a trusted environment, or when a malicious user exploits a software or configuration flaw. You must ensure that you trust the assemblies and other components you deploy in your environment. To minimize the possibility of an elevation of privileges attack, you should use non-overlapping, least permission accounts, and you should avoid the use of administrative accounts for run time services and operations. You should also minimize the number of components, applications, and services running in the environment.  
  
## See Also  
 [Mitigating Denial of Service Attacks](../core/mitigating-denial-of-service-attacks.md)   
 [Security Recommendations for a BizTalk Server Deployment](../core/security-recommendations-for-a-biztalk-server-deployment.md)   
 [Planning for Security](../core/planning-for-security.md)