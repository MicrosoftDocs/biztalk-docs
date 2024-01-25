---
description: "Learn more about: Ports for the BAM Portal Server"
title: "Ports for the BAM Portal Server"
ms.custom: ""
ms.date: "01/07/2016"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Ports for the BAM Portal Server
For complete information about securing your BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 The following table lists the ports you must configure for the BAM Portal Web site to access the services they need. The firewall on which you need to open the ports depends on where the destination server is in your architecture. You must open these ports both for inbound and outbound traffic.  
  
|Service or Application context|Destination Server|Destination Service|Port|Protocol|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Logged on user|BizTalk Management database|SQL Server|1433|TCP|To create and configure the database|  
|Logged on user|BizTalk Management database|DTC|135|TCP|Transacted connection to SQL Server for creating, configure, and update the database|  
|Logged on user|BizTalk Management database|DTC|49152-65535|TCP|Secondary RPC ports to create and connect to this database **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|Application pool|Inbound clients|HTTP(S)|80 or 443|TCP|For inbound traffic for the Web Site|  
|Logged on user|MessageBox database|SQL server|1433|TCP|To create and configure the database|  
|Logged on user|MessageBox database|DTC|135|TCP|Transacted connection to SQL Server for creating, configure, and update the database|  
|Logged on user|MessageBox database|DTC|49152-65535|TCP|Secondary RPC ports **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|SSO service account|SSO database|SQL server|1433|TCP|To connect to SSO database|  
|Logged on user|Tracking database|SQL Server|1433|TCP|To create and configure the database|  
|Logged on user|Business Rule Engine database|SQL Server|1433|TCP|To create and configure the database|  
|Logged on user|Business Rule Engine database|DTC|135|TCP|Transacted connection to SQL Server to create, configure, and update the database|  
|Logged on user|Business Rule Engine database|DTC|49152-65535|TCP|Secondary RPC ports **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|Logged on user|BAM Analysis database|OLAP|2393|TCP|To create and configure the database|  
|Logged on user|BAM Analysis database|OLAP Server file system|445|TCP|Create OLAP data file (.mdb) on the remote computer|  
|Logged on user|BAM Analysis database|OLAP|2725|TCP|To update and retrieve information from the database|  
|SSO service account|SSO database|SQL Server|1433|TCP|For the SSO service to update and retrieve information from the database|  
|SSO service account|Master secret server|Master secret server|135|TCP|Transacted connection to SQL Server for the SSO service to connect to the master secret server|  
|SSO Service|Master secret server|Secondary RPC|49152-65535|TCP|Secondary RPC ports for the SSO service to connect to the master secret server. **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
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
