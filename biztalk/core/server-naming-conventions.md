---
title: "Server Naming Conventions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "architecture, naming conventions"
  - "naming conventions, servers"
  - "installation, naming conventions"
ms.assetid: 98989c15-51d7-4a67-b054-abe6993a98a6
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Server Naming Conventions
For complete information about the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 The following table describes the servers in the diagram in the topic [Large Distributed Architecture](../core/large-distributed-architecture.md), and their functions.  
  
|Server name in diagram|Function|Description|  
|----------------------------|--------------|-----------------|  
|FW4|Firewall|Forefront Threat Management Gateway (TMG) 2010 server between the Internet and the perimeter network.|  
|HTTP (Receive)|Web Server|Web server that receives messages for the HTTP adapter. This server does not have BizTalk Server components installed; it has ASP.NET pages that relay the messages to the service interfaces domain. You can use Reverse Proxy from FW 4 to FW 3 instead of the ASP.NET pages. If you use Reverse Proxy, you do not need this server.|  
|Exchange (Send/Receive)|Mail Server|Mail server that BizTalk Server uses to send and receive SMTP messages. The POP3 Adapter reads the received messages|  
|FTP (Send/Receive)|Web Server|Represents the File Transport Protocol (FTP) server from which BizTalk is sending and receiving messages. This can be a remote server.|  
|SQL|SQL Server|Server with SQL Server database used by the SQL adapter.|  
|File|File Server|Server that has a file directory from which the File Adapter in the service interfaces domain drop and pick up files.|  
|FW3|Firewall|Forefront Threat Management Gateway (TMG) 2010 server protecting the service interfaces domain from the perimeter network and corporate domain.|  
|Processing|Processing Server|This server processes messages. It has the BizTalk Server runtime, Business Rule Engine, and Enterprise Single Sign-On (SSO) service. BizTalk assemblies, host instances, orchestrations, schemas, and maps are on this server. A given processing server can have host instances of different hosts.|  
|Receive handler<br /><br /> (Isolated Host)|Receive/Send Server|BizTalk Server dedicated to receiving messages from HTTP and SOAP adapters. A given receive/send server can have host instances of different hosts.|  
|Receive handler<br /><br /> (In-process Host)|Receive/Send Server|BizTalk Server dedicated to receiving messages from SQL, FTP, EDI, File, POP3 and BizTalk Message Queuing adapters. A given receive/send server can have host instances of different hosts.|  
|Send handler|Receive/Send Server|BizTalk Server dedicated to sending messages for all adapters. A given server can have host instances of different hosts you use for sending messages.|  
|FW2|Firewall|Forefront Threat Management Gateway (TMG) 2010 server protecting the services domain from the service interfaces and corporate domains (operation services.)|  
|Tracking Host|Tracking Server|Server that has a host instance of the BizTalk Host you use for tracking.|  
|Admin tools|Administration Server|Server that has the BizTalk Server runtime, the BizTalk Server Administration console, and the deployment tools.|  
|Master secret server|Master secret server|SSO Server that manages the master secret key for the whole environment. There are no other BizTalk Server components on this computer.|  
|FW1|Firewall|Forefront Threat Management Gateway (TMG) 2010 server protecting the data domain and the service interfaces and services domains.|  
|MessageBox 1<br /><br /> MessageBox 2<br /><br /> MessageBox 'n'|Data Server|SQL Server that contains the MessageBox databases. You can have a different SQL Server for each MessageBox database.|  
|SSO|Data Server|SQL Server that contains the SSO database, which Enterprise Single Sign-On uses to store in encrypted form user IDs and credentials for logging onto other systems, and for storing in encrypted form the configuration information form for adapters BizTalk Server uses.|  
|Backup/Restore for Log shipping|Data Server|SQL Server used to restore the database backups produced by BizTalk Server databases.|  
|BizTalk Analysis|Data Server|Analysis Server that contains the BizTalk Analysis database.|  
  
 The following table describes additional servers in the diagram in the topic [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md) and their functions compared to the diagram in the topic [Large Distributed Architecture](../core/large-distributed-architecture.md).  
  
|Server name|Function|Description|  
|-----------------|--------------|-----------------|  
|BAM Portal|BAM Portal|Server that contains BAM Portal. Business end users use the BAM portal to access the BAM databases to monitor Key Performance Indicators (KPIs) and other information about their business process.|  
|Notification Service<br /><br /> Windows SharePoint Services Configuration<br /><br /> Windows SharePoint Services Content<br /><br /> BAM Star Schema<br /><br /> BAM Primary Import<br /><br /> BAM Archive<br /><br /> BAM Analysis (OLAP)|IW Data Server|SQL Server that contains the databases used by Business Activity Monitoring. You can use multiple SQL Servers for these databases.|  
|IW clients|IW clients|Client computers that the information workers use for Business Activity Monitoring.|  
  
## See Also  
 [Large Distributed Architecture](../core/large-distributed-architecture.md)   
 [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md)