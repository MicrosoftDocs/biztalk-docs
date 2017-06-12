---
title: "Ports for the Enterprise Single Sign-On Servers | Microsoft Docs"
ms.custom: ""
ms.date: "2016-01-07"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ports, SSO"
  - "SSO"
ms.assetid: 30eb99f9-02cb-43c9-b038-d7bd898e3a7a
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ports for the Enterprise Single Sign-On Servers
For complete information about securing your BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 The following table lists the ports that an Enterprise Single Sign-On server in the processing domain need to access the master secret server and the SSO database. You must open these ports both for inbound and outbound traffic.  
  
|Service or Application context|Destination Server|Destination Service|Port|Protocol|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Logged on user|SSO database|SQL Server|1433|TCP|To create and connect to the SSO database.|  
|Single Sign-On service account|Master secret server|Single Sign-On service|135|TCP|Transacted connection to SQL Server for the Single Sign-On service to retrieve the master secret key from the master secret server|  
|Single Sign-On service account|Master secret server|Single Sign-On service|50000-50200|TCP|Secondary RPC ports used to retrieve the secret key from the master secret server. **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
  
 The following table lists the ports you must configure for the Enterprise Single Sign-On (SSO) master secret server to access the services it needs. The firewall on which you need to open the ports depends on where the destination server is in your architecture. You must open these ports both for inbound and outbound traffic.  
  
|Service or Application context|Destination Server|Destination Service|Port|Protocol|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|Logged on user|SSO database|SQL Server|1433|TCP|To create and connect to the SSO database.|  
|Single Sign-On service account|Processing server(s)|Single Sign-On service|135|TCP|Transacted connection to SQL Server for the Single Sign-On service to retrieve the master secret key from the master secret server|  
|Single Sign-On service account|Processing server(s)|Single Sign-On service|50000-50200|TCP|Secondary RPC ports used to retrieve the secret key from the master secret server. **Note:**  You may need to open more secondary RPC ports depending on your server load.|  
  
## See Also  
 [Server Naming Conventions](../core/server-naming-conventions.md)   
 [SSO Security Recommendations](../core/sso-security-recommendations.md)   
 [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md)