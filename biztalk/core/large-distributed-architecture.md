---
title: "Large Distributed Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "architecture, examples"
  - "data, domains"
  - "corporate domains"
  - "networks"
  - "domain types, service"
  - "domain types, processing"
  - "screened subnet"
  - "service domains"
  - "domain types, corporate"
  - "domain types, data"
  - "perimeter networks"
  - "processing domains"
  - "demilitarized zone"
  - "architecture, large distributions"
ms.assetid: 3cfc07c4-0b1d-489b-9a29-55187fde0539
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Large Distributed Architecture
For complete information about the system architecture for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 The architecture presented in this section is for a production environment. It does not include a development or test environment, or recommendations for a management network for the environment. For more information about staging your configuration from a development to a test environment, and from a test to a production environment, see [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md).  
  
 The following figure shows a highly distributed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architecture that takes into account defense in depth.  
  
 ![Large Distributed Architecture](../core/media/06c5ae00-17aa-42f5-88d1-487bf7720183.gif "06c5ae00-17aa-42f5-88d1-487bf7720183")  
Distributed BizTalk Server secure architecture  
  
 This architecture contains the following five domains:  
  
 **Perimeter network.** The perimeter network (also known as DMZ, demilitarized zone, and screened subnet), contains servers that provide Internet-related services for an enterprise. This domain can contain servers that are home to the physical locations where Internet-facing transports send and receive messages to and from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. There are no BizTalk Servers, BizTalk receive locations, or Enterprise Single Sign-On servers in this domain. If you use the SOAP or HTTP adapter, you can use reverse proxy rules (Forefront Threat Management Gateway (TMG) 2010 server implementation is called Web Publishing) to relay the message from the Internet-facing firewall (FW4) to the firewall protecting the service interfaces domain (FW3). For more information about Web Publishing rules, see the Microsoft Web site at [http://go.microsoft.com/fwlink/?LinkID=205340](http://go.microsoft.com/fwlink/?LinkID=205340) (<http://go.microsoft.com/fwlink/?LinkID=205340>).  
  
 In the preceding figure, the servers in the perimeter network represent servers that are in a domain outside of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. Therefore, some of these servers may alternatively be on remote locations. For example, the File Transfer Protocol (FTP) server could be on a remote location; the Simple Mail Transfer Protocol (SMTP) server could be the corporate e-mail server, an Internet service provider’s (ISP) server, or a remote SMTP server.  
  
 **Service Interfaces domain.** This is the domain where the message processing starts. This domain contains the servers that have the BizTalk receive and send handlers. This is where the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ports, receive locations, pipelines, maps, schemas, and assemblies are located to receive, route and send messages. The number of BizTalk Servers in this domain depends on the number of hosts and host instances you need for the performance requirements of your company.  
  
 **Services domain.** This domain contains the services that the servers in the service interfaces domain trust and need to process messages successfully, but that require a further layer of defense from attacks from the perimeter network such as the processing servers that have the BizTalk orchestrations, pipelines, Enterprise Single Sign-On (SSO) services, Business Rule Engine, and other business processes.  
  
 This domain also contains the services that the corporate domain needs to access, but that you still need to protect from external threats. One of the servers in this domain hosts the administration tools: BizTalk Administration Console and the Enterprise Single Sign-On (SSO) administration utility. This domain also contains the SSO master secret server, which holds the master secret (encryption key) that the SSO system uses to encrypt the data in the SSO database. One of the servers in this domain has a host instance of a host that supports tracking of health monitoring and business monitoring data.  
  
> [!NOTE]
>  In an Enterprise Single Sign-On system, some of the processing servers may contain only the SSO service with no BizTalk Server components. For more information, see [High Availability for Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).  
  
 **Data domain.** The data domain is the furthest away from the Internet, as it contains the SQL Server databases that store critical business and process data, and it does not trust any other domain. While you can have each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database on a different server running SQL Server, we recommend combining databases based on the main type of processing they do (mostly read operations, mostly write operations, or both):  
  
- A SQL Server for each MessageBox database. You can add more MessageBox databases for load balancing. These are read- and write-intensive databases.  
  
- A SQL Server for the SSO database. BizTalk Server does mostly read operations in this database. This database holds sensitive data, and needs the most restrictive access permissions.  
  
- A SQL Server for the BizTalk Management, and the Business Rule Engine databases. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does mostly read operations in these databases. This server also contains the Tracking database, which is a write-intensive database.  
  
- A SQL Server for the Analysis Server Tracking database.  
  
- A SQL Server for the Microsoft Operations Manager (MOM) database.  
  
- A SQL Server for the destination system for log shipping  
  
> [!IMPORTANT]
>  For failover protection, we recommend you cluster each BizTalk database. For more information about SQL Server failover clustering, see the Microsoft MSDN Web Site at [http://go.microsoft.com/fwlink/?LinkId=131016](http://go.microsoft.com/fwlink/?LinkId=131016).  
  
> [!NOTE]
>  For more information about the destination system for log shipping, see [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md).  
  
 In the preceding figure, Forefront Threat Management Gateway (TMG) 2010 server acts as a software firewall to protect and contain each of these domains. In addition, each domain has its own domain controller, with trust established from the domain that contains the critical servers (data domain) to the outward-facing servers (perimeter network and corporate domain), and servers have access only to the services in other domains that they need to connect to. There is one firewall restricting traffic to the data domain from both the service interfaces and services domains (FW1). Similarly, there is one firewall (FW2) restricting traffic to the services domain, both from the service interfaces and operation domains.  
  
 **Corporate domain.** This is the intranet domain, and it contains all the desktop computers within your company or department, and all the servers that provide services to the information workers within your company. There are two distinct logical containers within this domain:  
  
- **Intranet services.** This container has the servers that receive and send messages to and from internal partners for the SQL and File adapters. While this is an intranet, it is different from the corporate network where most users have their accounts and services. Similar to the perimeter network in the figure, some of the servers in this container can be on a different location. For example, the send and receive location (folder) for the File adapter can be in any tier outside of the service interfaces domain, while you can place the server running SQL Server for the SQL adapter on the service interfaces domain.  
  
- **Operations.** This container has the Terminal Service clients the IT Professionals use to remotely administer, maintain, and monitor the performance and health of all the servers in the environment. By using Terminal Services, IT professionals connect to the administration server in the services domain, and from there perform administrative tasks for all the servers in the environment.  
  
  Although you may have development computers within the corporate domain, the configuration of those computers does not fall within the scope of this document.  
  
  For more information about the BizTalk Server architecture including the information worker services, see [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md).  
  
  The trust between the domains is as follows:  
  
- The data domain does not trust any other domain.  
  
- The service interfaces domain trusts the data domain.  
  
- The services domain trusts the data domain.  
  
- The corporate domain trusts the services domains.  
  
  For more information about configuring a firewall for domains and trusts, see the Microsoft Help and Support Web site at [http://go.microsoft.com/fwlink/?LinkId=25230](http://go.microsoft.com/fwlink/?LinkId=25230).  
  
  While the preceding figure focuses on security, you can also extend the architecture with Network Load Balancing (NLB) and Clustering Services for availability and performance.  
  
  For more information about high availability, see [Planning for High Availability](../core/planning-for-high-availability3.md).  
  
  For more information about performance, see [Planning for Sustained Performance](../core/planning-for-sustained-performance.md).  
  
  The following table summarizes the type of servers you can configure with Network Load Balancing (NLB) depending on the Service Level Agreement (SLA) that you need achieve:  
  
|Name|Type|Domain|  
|----------|----------|------------|  
|HTTP (Rec)|Internet Information Services|Perimeter Network|  
|Receive Handler (Isolated)|Internet Information Services|Service Interfaces Domain|  
|BAM Portal|Internet Information Services|Service Interfaces Domain|  
  
 The following table summarizes the type of servers you can cluster depending on the Service Level Agreement (SLA) that you need achieve:  
  
|Name|Type|Domain|  
|----------|----------|------------|  
|Exchange (Send)|Exchange Server|Perimeter Network|  
|Receive Handler (In-process host) for FTP and POP3 Adapters|BizTalk Server|Service Interfaces Domain<br /><br /> Corporate Domain|  
|Master secret server|BizTalk Server|Services Domain|  
|All SQL Servers|SQL Server|Data Domain|  
  
 For more information about the BizTalk Server architecture including the information worker services, see [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md).  
  
## See Also  
 [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md)   
 [Scaled Down Architecture](../core/scaled-down-architecture.md)