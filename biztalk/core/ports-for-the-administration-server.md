---
description: "Learn more about: Ports for the Administration Server"
title: "Ports for the Administration Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Ports for the Administration Server
For complete information about securing your BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 The following table lists the ports you must configure for the administration server to access the services they need. The firewall on which you need to open the ports depends on where the destination server is in your architecture. 
  
|Destination Server|Destination Service|Port|Protocol|Reason|  
|---|---|---|---|---|  
|BizTalk Management database|SQL Server|1433|TCP|To create, configure, and access information in the BizTalk Management database|  
|BizTalk Management database|DTC|135|TCP|Transacted connection to SQL Server to update the database. RPC endpoint manager.|  
|BizTalk Management database|DTC|49152-65535|TCP|Secondary RPC ports **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|BAM Primary Import database|SQL Server|1433|TCP|To verify the BAM Primary Import database exists by using the BizTalk Administration console (or WMI)|  
|BizTalk Management database|SQL Server|1433|TCP|To view configuration data and install host instances by using the BizTalk Administration console (or WMI)|  
|BizTalk Management database|DTC|135|TCP|Transacted connection to SQL Server to create and update a host by using the BizTalk Administration console (or WMI)|  
|BizTalk Management database|DTC|49152-65535|TCP|Secondary RPC ports to create a host by using the BizTalk Administration console (or WMI) **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|MessageBox database|SQL Server|1433|TCP|To create a host by using the BizTalk Administration console (or WMI)|  
|MessageBox database|DTC|135|TCP|Transacted connection to SQL Server to create and update a host by using the BizTalk Administration console (or WMI)|  
|MessageBox database|DTC|49152-65535|TCP|Secondary RPC ports to create a host by using the BizTalk Administration console (or WMI) **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|Processing server|WMI/RPC|135|TCP|Transacted connection to SQL Server to add a new server to the group by using the BizTalk Administration console (or WMI)|  
|Processing server|WMI/RPC|49152-65535|TCP|Secondary RPC ports to add a new server to the group by using the BizTalk Administration console (or WMI) **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|Processing server|Server Message Block (SMB)|445|TCP|Used to access file shares. May also be needed to install a host instance using the BizTalk Administration console (or WMI).|  
|Business Rule Engine database|SQL Server|1433|TCP|To deploy business rules by using the Business Rule Engine Deployment Wizard|  
|Business Rule Engine database|DTC|135|TCP|Transacted connection to SQL Server to deploy business rules by using the Business Rule Engine Deployment Wizard|  
|Business Rule Engine database|DTC|49152-65535|TCP|Secondary RPC ports to deploy business rules by using the Business Rule Engine Deployment Wizard. **Note:**  You can change to larger dynamic port range or better use fixed port for MSDTC and EntSSO services.|  
|BizTalk Management database|SQL Server|1433|TCP|To deploy an assembly|  
|Tracking database|SQL Server|1433|TCP|To deploy an assembly|  
|IIS Server|IIS|1164|TCP|To enable BizTalk application deployment to pack HTTP or Web Service Ports hosted on the IIS Server into an MSI.|  
  
## See Also  
 [Server Naming Conventions](../core/server-naming-conventions.md)   
 [Application Deployment Security Recommendations](../core/application-deployment-security-recommendations.md)   
 [Security Considerations for Message and Instance Data Tracking](../core/security-considerations-for-message-and-instance-data-tracking.md)   
 [Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md)   
 [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md)
