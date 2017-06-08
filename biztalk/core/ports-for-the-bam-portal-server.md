---
title: "Ports for the BAM Portal Server | Microsoft Docs"
ms.custom: ""
ms.date: "2016-01-07"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df67c31c-a7a3-4bff-9374-0d8a0cf0ad21
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ports for the BAM Portal Server
For complete information about securing your BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 The following table lists the ports you must configure for the BAM Portal Web site to access the services they need. The firewall on which you need to open the ports depends on where the destination server is in your architecture. You must open these ports both for inbound and outbound traffic.  
  
|Service or Application context|Destination Server|Destination Service|Port|Protocol|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Logged on user|BizTalk Management database|SQL Server|1433|TCP|To create and configure the database|  
|Logged on user|BizTalk Management database|DTC|135|TCP|Transacted connection to SQL Server for creating, configure, and update the database|  
|Logged on user|BizTalk Management database|DTC|50000-50200|TCP|Secondary RPC ports to create and connect to this database **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|Application pool|Inbound clients|HTTP(S)|80 or 443|TCP|For inbound traffic for the Web Site|  
|Logged on user|MessageBox database|SQL server|1433|TCP|To create and configure the database|  
|Logged on user|MessageBox database|DTC|135|TCP|Transacted connection to SQL Server for creating, configure, and update the database|  
|Logged on user|MessageBox database|DTC|50000-50200|TCP|Secondary RPC ports **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|SSO service account|SSO database|SQL server|1433|TCP|To connect to SSO database|  
|Logged on user|Tracking database|SQL Server|1433|TCP|To create and configure the database|  
|Logged on user|Business Rule Engine database|SQL Server|1433|TCP|To create and configure the database|  
|Logged on user|Business Rule Engine database|DTC|135|TCP|Transacted connection to SQL Server to create, configure, and update the database|  
|Logged on user|Business Rule Engine database|DTC|50000-50200|TCP|Secondary RPC ports **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|Logged on user|BAM Analysis database|OLAP|2393|TCP|To create and configure the database|  
|Logged on user|BAM Analysis database|OLAP Server file system|445|TCP|Create OLAP data file (.mdb) on the remote computer|  
|Logged on user|BAM Analysis database|OLAP|2725|TCP|To update and retrieve information from the database|  
|SSO service account|SSO database|SQL Server|1433|TCP|For the SSO service to update and retrieve information from the database|  
|SSO service account|Master secret server|Master secret server|135|TCP|Transacted connection to SQL Server for the SSO service to connect to the master secret server|  
|SSO Service|Master secret server|Secondary RPC|50000-50200|TCP|Secondary RPC ports for the SSO service to connect to the master secret server. **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
|BizTalk Host instance|MessageBox database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
|BizTalk Host instance|BizTalk Management database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
|BizTalk Host instance|SSO database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
|BizTalk Host instance|Tracking database|SQL Server|1433|TCP|To update and retrieve information from the database during run time operations|  
|BAM Application Pool User|BAM Notification Services|SQL Server|1433|TCP|To access BAM Notification Services database|  
  
## See Also  
 [Server Naming Conventions](../core/server-naming-conventions.md)   
 [Security Considerations for the BAM Portal](../core/security-considerations-for-the-bam-portal.md)   
 [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md)