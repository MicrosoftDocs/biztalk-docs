---
description: "Learn more about: Ports for the Receive and Send Servers"
title: "Ports for the Receive and Send Servers | Microsoft Docs"
ms.custom: ""
ms.date: "01/07/2016"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connection strings"
  - "servers, sending"
  - "ports, servers"
  - "servers, receiving"
  - "BizTalk Server, service accounts"
  - "SSO, service accounts"
ms.assetid: 19cafe74-6676-4779-8ced-de0841dba19f
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ports for the Receive and Send Servers
For complete information about securing your BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 The following table lists the ports you must configure for the receive and send servers to access the services they need. The firewall on which you need to open the ports depends on where the destination server is in your architecture. You must open these ports both for inbound and outbound traffic.  
  
|Service or Application context|Destination Server|Destination Service|Port|Protocol|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|BizTalk service account|File share<br /><br /> EDI documents home share|Receive/Send server|445|TCP|Retrieve and drop files to file location for the File adapter|  
|BizTalk service account|FTP Server|FTP service|20|TCP|For the FTP adapter to retrieve and drop files to FTP Server|  
|BizTalk service account|FTP Server|FTP service|21|TCP|For the FTP adapter to retrieve and drop files to FTP Server|  
|BizTalk service account|POP3 Server|POP3 service|110|TCP|For the POP3 adapter to retrieve email from POP3 Server|  
|BizTalk service account|Processing Server|Windows Message Queuing|1801|TCP|For the BizTalk Message Queuing adapter to receive and send messages to the BizTalk runtime|  
|Connection string|SQL adapter target|SQL Server|1433|TCP|Retrieve and send messages from databases used by SQL adapter|  
|Connection string|SQL adapter target|DTC|135|TCP|Transacted connection to SQL Server for SQL adapter|  
|Connection string|SQL adapter target|DTC|50000-50200|TCP|Secondary RPC ports for SQL adapter **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|BizTalk service account|SMTP/Exchange|SMTP|25|TCP|For the SMPT adapter to connect to SMTP server|  
|Logged on user|BizTalk Management database|SQL Server|1433|TCP|To create and configure the BizTalk Management database|  
|Logged on user|BizTalk Management database|DTC|135|TCP|Transacted connection to SQL Server to create, configure, and update the database|  
|Logged on user|BizTalk Management database|DTC|50000-50200|TCP|Secondary RPC ports **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|Logged on user|MessageBox database|SQL Server|1433|TCP|To create and configure the MessageBox database|  
|Logged on user|MessageBox database|DTC|135|TCP|Transacted connection to SQL Server to create the host|  
|Logged on user|MessageBox database|DTC|50000-50200|TCP|Secondary RPC ports **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|SSO service account|SSO database|SQL Server|1433|TCP|For the Enterprise Single Sign-On service to connect to the SSO database|  
|Logged on user|SSO database|DTC|135|TCP|Transacted connection to SQL Server to connect to the SSO database|  
|Logged on user|SSO database|DTC|50000-50200|TCP|Secondary RPC ports **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|Logged on user|Tracking database|SQL Server|1433|TCP|To create and configure the Tracking database|  
|Logged on user|Tracking database|DTC|135|TCP|Transacted connection to SQL Server|  
|Logged on user|Tracking database|DTC|50000-50200|TCP|Secondary RPC ports **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|Logged on user|Business Rule Engine database|SQL Server|1433|TCP|To create and configure the Business Rule Engine database|  
|Logged on user|Business Rule Engine database|DTC|135|TCP|Transacted connection to SQL Server to create, configure, and update the database|  
|Logged on user|Business Rule Engine database|DTC|50000-50200|TCP|Secondary RPC ports **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|Logged on user|BAM Analysis database|OLAP|2383 (SQL Server 2005 Analysis Services)|TCP|To update and retrieve information from the BAM Analysis database|  
|Logged on user|BAM Analysis database|OLAP Server File system|445|TCP|To create the OLAP data file (.mdb) on the remote computer|  
|Logged on user|BAM Analysis database|OLAP|2725|TCP|For data retrieval for analysis (PivotTable® reports)|  
|Logged on user|BizTalk Analysis database|OLAP|2383 (SQL Server 2005 Analysis Services)|TCP|To create and configure the BizTalk Analysis database **Note:**  The Processing Servers need to connect to this database only when you run the BizTalk Configuration Manager.|  
|Logged on user|BizTalk Analysis database|OLAP Server File system|445|TCP|To create the OLAP data file (.mdb) on the remote computer **Note:**  The Processing Servers need to connect to this database only when you run the BizTalk Configuration Manager.|  
|Logged on user|BizTalk Analysis database|OLAP|2725|TCP|To create and configure the database, and to retrieve data for analysis (PivotTable reports)|  
|Single Sign-On service account|Master secret server|RPC|135|TCP|Transacted connection to SQL Server for the SSO service to connect to the master secret server|  
|Single Sign-On service account|Master secret server|Secondary RPC|50000-50200|TCP|Secondary RPC ports for the SSO service to connect to the master secret server. **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|Service account for a BizTalk Host instance|MessageBox database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
|Service account for a BizTalk Host instance|BizTalk Management database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
|Service account for a BizTalk Host instance|SSO database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
|Service account for a BizTalk Host instance|Tracking database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
  
## See Also  
 [Server Naming Conventions](../core/server-naming-conventions.md)   
 [HTTP Adapter Security Recommendations](../core/http-adapter-security-recommendations.md)   
 [SOAP Adapter Security Recommendations](../core/soap-adapter-security-recommendations.md)   
 [FTP Adapter Security Recommendations](https://msdn.microsoft.com/library/ea7c0577-9d72-4d63-94e7-8f649c6e713f)   
 [SMTP Adapter Security Recommendations](../core/smtp-adapter-security-recommendations.md)   
 [File Adapter Security Recommendations](https://msdn.microsoft.com/library/fe4d51c0-b697-457b-bf27-f1cf6965d954)   
 [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md)
