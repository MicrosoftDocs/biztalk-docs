---
title: "Sample Architecture: Base BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "architecture, examples"
  - "IPSec"
  - "BizTalk Server, examples"
  - "security, examples"
  - "security, architecture"
  - "IPSec, about IPSec"
  - "BizTalk Server, architecture"
  - "architecture, security"
ms.assetid: 7ccc1ef3-670f-423f-b6ca-3d56b9bbeabf
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sample Architecture: Base BizTalk Server
This topic discusses the base sample architecture. It describes the components in a BizTalk Server deployment that are adapter-independent. We recommend that any BizTalk Server deployment have at least these components.  
  
 The following figure shows the components of the base BizTalk Server sample architecture. These components appear in all the adapter-specific BizTalk Server architectures that we discuss in later sections.  
  
 **Figure 1 Base architecture components**  
  
 ![Base architecture components](../core/media/tdi-sec-refarch.gif "TDI_Sec_RefArch_")  
  
 This sample architecture contains the items discussed in the following sections.  
  
## Perimeter network―internet  
  
-   This perimeter network (also known as DMZ, demilitarized zone, and screened subnet) contains servers that provide Internet-related services. There are no BizTalk Servers, BizTalk receive locations, or Enterprise Single Sign-On servers in this domain.  
  
## Perimeter network―intranet  
 This perimeter network contains servers that provide intranet-related services. It provides an additional layer of security between your intranet (for example, a corporate network) and the servers that run the application. Like the Internet perimeter network, the intranet perimeter network does not contain BizTalk Servers, BizTalk receive locations, or Enterprise Single Sign-On servers.  
  
## E-Business Domain  
 This domain contains all the infrastructure and applications used by your BizTalk Server implementation. The servers in this domain are:  
  
-   **BizTalk Server.** This server has an installation of the BizTalk Server runtime and instances of various BizTalk Hosts. The number of BizTalk Servers in the environment depends on the type of hosts they run and the performance needs. As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.  
  
-   **Master secret server.** This server is the Enterprise Single Sign-On (SSO) master secret server. It holds the master secret (encryption key) that the SSO system uses to encrypt the data in the SSO database.  
  
-   **SQL Server.** This server contains the BizTalk databases.  
  
    > [!IMPORTANT]
    >  For failover protection, we recommend that you cluster each BizTalk database. For more information about Microsoft SQL Server failover clustering, see the Microsoft MSDN Web site at [http://go.microsoft.com/fwlink/?LinkID=190216](http://go.microsoft.com/fwlink/?LinkID=190216).  
  
    > [!NOTE]
    >  Depending on your performance needs, you might have to separate the BizTalk databases into multiple computers that run SQL Server.  
  
-   **Domain controller.** This server hosts the E-Business Active Directory domain. It contains information about all the groups and individual accounts that need access to BizTalk Server.  
  
-   **Administration tools.** One of the servers in this domain hosts the administration tools: BizTalk Administration console and Enterprise Single Sign-On (SSO) administration utility.  
  
## Firewalls and Domains  
 In Figure 1, Forefront Threat Management Gateway (TMG) 2010 server acts as a software firewall to help protect and contain each of these domains. Additionally, the E-Business domain has its own domain controller, and this domain does not trust any other domain. For more information about how to configure a firewall for domains and trusts, see the Microsoft Help and Support Web site at [http://go.microsoft.com/fwlink/?LinkId=25230](http://go.microsoft.com/fwlink/?LinkId=25230).  
  
 The sample architecture has two firewalls:  
  
- **Firewall 1.** This firewall has three network interfaces: It routes traffic from the Internet, the intranet, and the perimeter networks.  
  
- **Firewall 2.** This firewall is dual-homed: It routes traffic from the perimeter networks (both Internet and intranet) and the E-Business domain.  
  
  The computers in the perimeter networks are not members of any domain, and they do not communicate with each other.  
  
## IPsec  
 We recommend that you use Internet Protocol security (IPSec) to help secure the communication between all the servers in the E-Business domain. The IPsec rules are as follows:  
  
- Allow authenticated traffic between BizTalk Server and the domain controller.  
  
- Allow authenticated traffic between BizTalk Server and the administration tools server.  
  
- Allow authenticated traffic between BizTalk Server and the master secret server.  
  
- Allow authenticated traffic between BizTalk Server and the SQL Server.  
  
- Allow authenticated traffic between the master secret server and the domain controller.  
  
- Allow authenticated traffic between the master secret server and the BizTalk Server (isolated, processing, in-process, and tracking hosts.)  
  
- Allow authenticated traffic between the master secret server and the SQL Server (SSO databases).  
  
- Allow authenticated traffic between the domain controller and all the servers in the domain.  
  
- Allow authenticated traffic between the administration tools server and all the servers in the domain.  
  
  If you have other applications in the domain that do not need access to the BizTalk Server, SQL Server, master secret server, or administration tools server, block traffic between those applications and the appropriate servers.  
  
## See Also  
 [Planning for Security](../core/planning-for-security.md)   
 [Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [Sample Scenarios for Threat Model Analysis](../core/sample-scenarios-for-threat-model-analysis.md)