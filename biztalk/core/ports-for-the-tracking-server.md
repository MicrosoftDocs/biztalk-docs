---
description: "Learn more about: Ports for the Tracking Server"
title: "Ports for the Tracking Server | Microsoft Docs"
ms.custom: ""
ms.date: "01/07/2016"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tracking server"
  - "ports, tracking server"
ms.assetid: 4b4913a4-7d8d-4fd0-a116-ba868c4ad7da
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ports for the Tracking Server
For complete information about securing your BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 The following table lists the ports you must configure for the tracking server to access the services they need. The firewall on which you need to open the ports depends on where the destination server is in your architecture. You must open these ports both for inbound and outbound traffic.  
  
|Service or Application context|Destination Server|Destination Service|Port|Protocol|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Logged on user|BizTalk Management database|SQL Server|1433|TCP|To create and configure the BizTalk Management database|  
|Logged on user|BizTalk Management database|DTC|135|TCP|Transacted connection to SQL Server to update and retrieve information from the database. RPC endpoint manager.|  
|Logged on user|BizTalk Management database|DTC|49152-65535|TCP|Secondary RPC ports **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|Logged on user|SSO database|SQL Server|1433|TCP|For the SSO Service to connect to the SSO database|  
|Logged on user|BAM Primary Import database|SQL Server|1433|TCP|To validate the BAM Primary Import database. The Tracking host connects to this database during run time.|  
|Logged on user|BAM Star Schema database|SQL Server|1433||To update and retrieve information from the database. **Note:**  The Tracking host connects to this database only when you run the BizTalk Configuration Manager to create a new BizTalk group from this server.|  
|Logged on user|BAM Analysis database|OLAP|445|TCP|To create the OLAP data file (.mdb) on the remote computer. **Note:**  The Tracking host connects to this database only when you run the BizTalk Configuration Manager to create a new BizTalk group from this server.|  
|Logged on user|BAM Analysis database|OLAP|2383 (SQL Server 2005 Analysis Services)||To create and configure the BAM Analysis database **Note:**  The Tracking host connects to this database only when you run the BizTalk Configuration Manager to create a new BizTalk group from this server.|  
|Logged on user|BAM Analysis database|OLAP|2725|TCP|For data retrieval for analysis (PivotTable reports) **Note:**  The Tracking host connects to this database only when you run the BizTalk Configuration Manager to create a new BizTalk group from this server.|  
|Logged on user|Tracking database|SQL Server|1433|TCP|To update and retrieve information from the database|  
|Logged on user|MessageBox database|SQL|1433|TCP|To update and retrieve information from the database|  
|Logged on user|MessageBox database|DTC|135|TCO|Transacted connection to SQL Server. RPC endpoint manager.|  
|Logged on user|MessageBox database|DTC|49152-65535||Secondary RPC ports|  
|Logged on user|BAM Archive database|SQL Server|1433|TCP|To update and retrieve information from the database **Note:**  The Tracking host connects to this database only when you run the BizTalk Configuration Manager to create a new BizTalk group from this server.|  
|SSO service account|SSO database|SQL Server|1433|TCP|To update and retrieve information from the database|  
|SSO service account|Master secret server|Master Secret service|135|TCP|Transacted connection to SQL Server for the SSO service to connect to the master secret server. RPC endpoint manager.|  
|SSO service account|Master secret server|Secondary RPC|49152-65535|TCP|Secondary RPC ports for SSO service to connect to the master secret server|  
  
## See Also  
 [Server Naming Conventions](../core/server-naming-conventions.md)   
 [Security Considerations for Message and Instance Data Tracking](../core/security-considerations-for-message-and-instance-data-tracking.md)   
 [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md)   
 [BizTalk Server What's New, Install, Configuration, and Upgrade](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)
