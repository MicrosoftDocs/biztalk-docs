---
description: "Learn more about: Ports for the Processing Servers"
title: "Ports for the Processing Servers | Microsoft Docs"
ms.custom: ""
ms.date: "01/07/2016"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servers, processing"
  - "ports, processing servers"
ms.assetid: 0207b68f-8769-4674-aadc-b3a67b6f210b
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ports for the Processing Servers
For complete information about securing your BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 The following table lists the ports you must configure for the processing servers to access the services they need. The firewall on which you need to open the ports depends on where the destination server is in your architecture. You must open these ports both for inbound and outbound traffic.  
  
|Service or Application context|Destination Server|Destination Service|Port|Protocol|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Logged on user|BizTalk Management database|SQL Server|1433|TCP|To create and configure the BizTalk Management database|  
|Logged on user|BizTalk Management database|DTC|135|TCP|Transacted connection to SQL Server to create, configure, and update the database|  
|Logged on user|BizTalk Management database|DTC|49152-65535|TCP|Secondary RPC ports **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|Logged on user|MessageBox database|SQL Server|1433|TCP|To create and configure the MessageBox database|  
|Logged on user|MessageBox database|DTC|135|TCP|Transacted connection to SQL Server to create the host|  
|Logged on user|MessageBox database|DTC|49152-65535|TCP|Secondary RPC ports **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|SSO service account|SSO database|SQL Server|1433|TCP|For the Enterprise Single Sign-On service to connect to the SSO database|  
|Logged on user|SSO database|DTC|135|TCP|Transacted connection to SQL Server to connect to the SSO database|  
|Logged on user|SSO database|DTC|49152-65535|TCP|Secondary RPC ports **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|Logged on user|Tracking database|SQL Server|1433|TCP|To create and configure the Tracking database|  
|Logged on user|Tracking database|DTC|135|TCP|Transacted connection to SQL Server|  
|Logged on user|Tracking database|DTC|49152-65535|TCP|Secondary RPC ports **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|Logged on user|Business Rule Engine database|SQL Server|1433|TCP|To create and configure the Business Rule Engine database|  
|Logged on user|Business Rule Engine database|DTC|135|TCP|Transacted connection to SQL Server to create, configure, and update the database|  
|Logged on user|Business Rule Engine database|DTC|49152-65535|TCP|Secondary RPC ports **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|Logged on user|BAM Analysis database|OLAP|2393|TCP|To update and retrieve information from the BAM Analysis database|  
|Logged on user|BAM Analysis database|OLAP Server File system|445|TCP|To create the OLAP data file (.mdb) on the remote computer|  
|Logged on user|BAM Analysis database|OLAP|2725|TCP|For data retrieval for analysis (PivotTable reports)|  
|Logged on user|BizTalk Analysis database|OLAP|2393|TCP|To create and configure the BizTalk Analysis database **Note:**  The processing servers need to connect to this database only when you run the BizTalk Configuration Manager.|  
|Logged on user|BizTalk Analysis database|OLAP Server File system|445|TCP|To create the OLAP data file (.mdb) on the remote computer **Note:**  The processing servers need to connect to this database only when you run the BizTalk Configuration Manager.|  
|Logged on user|BizTalk Analysis database|OLAP|2725|TCP|To create and configure the database, and to retrieve data for analysis (PivotTable reports)|  
|Single Sign-On service account|Master secret server|RPC|135|TCP|Transacted connection to SQL Server for the SSO service to connect to the master secret server|  
|Single Sign-On service account|Master secret server|Secondary RPC|49152-65535|TCP|Secondary RPC ports for the SSO service to connect to the master secret server. **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|Service account for a BizTalk Host instance|MessageBox database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
|Service account for a BizTalk Host instance|BizTalk Management database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
|Service account for a BizTalk Host instance|SSO database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
|Service account for a BizTalk Host instance|Tracking database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
  
## See Also  
 [Server Naming Conventions](../core/server-naming-conventions.md)   
 [BizTalk Server Runtime Security Recommendations](../core/biztalk-server-runtime-security-recommendations.md)   
 [Business Rule Engine Security Recommendations](../core/business-rule-engine-security-recommendations.md)   
 [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md)
