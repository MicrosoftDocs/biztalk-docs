---
title: "Transaction Integrator Threat Mitigation2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68854feb-caab-488f-83f0-2da7d2e4cb01
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Transaction Integrator Threat Mitigation
Product security is a top priority across Microsoft. Beginning with the Windows Security Push in 2002, Microsoft has invested additional time and resources to developing more secure code and detailed instructions for deploying and securing your computing environment. The [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] product team conducted a complete threat modeling analysis to identify and mitigate potential areas of concern. A threat model is a security-based analysis that helps you determine the highest-level security risks posed to a product or application and how attacks can manifest themselves.  
  
 Although Microsoft has mitigated all possible internal security threats to [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], there are steps you should take to mitigate threats from elsewhere in your network environment. Threat modeling helps you evaluate the threats to the applications you are writing or running, and thereby reduce the overall risk to your computer system. For more information about threat model analysis, see Chapter 4 Threat Modeling in Michael Howard and David LeBlanc, *Writing Secure Code 2nd Edition*, Redmond, WA: Microsoft Press. 2003.  
  
 Howard and LeBlanc summarize six categories of possible security threats to your computing environment:  
  
- **Spoofing identity**. Spoofing threats allow an attacker to pose as another user or allow a rogue server to pose as a valid server. An example of user identity spoofing is illegally accessing and then using another users authentication information, such as username and password.  
  
- **Tampering with data**. Data tampering involves malicious modification of data. Examples include unauthorized changes made to persistent data, such as that held in a database, and the alteration of data as it flows between two computers over an open network, such as the Internet.  
  
- **Repudiation**. Repudiation threats are associated with users who deny performing an action without other parties having any way to prove otherwise—for example, a user performing an illegal operation in a system that lacks the ability to trace the prohibited operations.  
  
- **Information disclosure**. Information disclosure threats involve the exposure of information to individuals who are not supposed to have access to it—for example, a users ability to read a file that she was not granted access to and an intruders ability to read data in transit between two computers.  
  
- **Denial of service**. Denial of service (DoS) attacks deny service to valid users— for example, by making a Web server temporarily unavailable or unusable. You must protect against certain types of DoS threats simply to improve system availability and reliability.  
  
- **Elevation of privileges**. In this type of threat, an unprivileged user gains privileged access and thereby has sufficient access to compromise or destroy the entire system. Elevation of privilege threats include those situations in which an attacker has effectively penetrated all system defenses and become part of the trusted system itself, a dangerous situation indeed.  
  
  Howard and LeBlanc also point out that some threat types can interrelate. For example, it is possible for information disclosure threats to lead to spoofing threats if the users credentials are not secured. Similarly, elevation of privilege threats are by far the worst because if someone can become an administrator or root on the target computer, every other threat category becomes a reality. Conversely, spoofing threats might lead to a situation where escalation is no longer needed for an attacker to achieve his goal.  
  
  To mitigate threats that originate outside Transaction Integrator but which can negatively affect TI components and your application, Microsoft recommends that you do the following:  
  
- [Protect the MSHIS60_HIP Database and SQL Server Stored Procedures](../core/protect-the-mshis60-hip-database-and-sql-server-stored-procedures1.md)  
  
- [Protect the COM+ and .NET Servers](../core/protect-the-net-servers1.md)  
  
- [Protect the Raw User Data](../core/protect-the-raw-user-data1.md)  
  
- [Protect the HIP Listener](../core/protect-the-hip-listener2.md)  
  
- [Protect the Local File System, Database, and Registry](../core/protect-the-local-file-system-database-and-registry1.md)  
  
- [Protect the Client Proxy](../core/protect-the-client-proxy1.md)  
  
- [Protect the Remoting Session](../core/protect-the-remoting-session1.md)  
  
- [Protect TI from Unauthorized Mainframe or AS/400 Access](../core/protect-ti-from-unauthorized-mainframe-or-as-400-access1.md)  
  
- [Protect the TI Runtime Environment](../core/protect-the-ti-runtime-environment1.md)  
  
- [Protect Mainframe Security Credentials from Being Overridden](../core/protect-mainframe-security-credentials-from-being-overridden1.md)  
  
- [Protect the TI Runtime and Host Environments from Data Overflows](../core/protect-the-ti-runtime-and-host-environments-from-data-overflows2.md)  
  
- [Protecting the TI .NET Assembly from Unauthorized Access](../core/protecting-the-ti-net-assembly-from-unauthorized-access2.md)  
  
- [Protecting the Output from Tracing and Network Monitoring Activities](../core/protecting-the-output-from-tracing-and-network-monitoring-activities2.md)  
  
- [Protecting the TI Record or Playback Files from Unauthorized Access](../core/protecting-the-ti-record-or-playback-files-from-unauthorized-access1.md)  
  
## See Also  
 [Application Integration (Security)](../core/application-integration-security-2.md)