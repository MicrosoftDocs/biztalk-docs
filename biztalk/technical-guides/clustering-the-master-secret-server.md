---
title: "Clustering the Master Secret Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14aa3622-8462-4ed9-abde-40090d4f96ff
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Clustering the Master Secret Server
The BizTalk Server application service maintains a hard-coded dependency upon the Enterprise Single Sign-On (SSO) service that is installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The SSO service must be able to communicate with the master secret server to start. We recommend that you cluster the SSO service on the master secret server to provide fault tolerance for the master secret server. For more information, see [High-Availability SSO Installation Options](http://go.microsoft.com/fwlink/?LinkId=156838) (<http://go.microsoft.com/fwlink/?LinkId=156838>) in BizTalk Server Help.  
  
## Preparing for Clustering the Master Secret Server  
  
### Deciding Whether to Use a Dedicated Cluster or the SQL Server Cluster  
 Clustering hardware is expensive. To reduce the hardware resources for a highly available solution, you can add the master secret server as a cluster resource in your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database cluster. If you use the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database cluster, we recommend that you do not put the master secret server on the same active node as the MessageBox database. The MessageBox database is usually busier than other databases. Even though the master secret server doesn't consume many hardware resources, it is better to move it to a different active cluster node from the active MessageBox database node.  
  
### Clustering the SSO Database  
 The master secret server depends on the SSO database. To build a high-availability SSO, you must cluster the SSO database. For more information about clustering BizTalk databases, see [Clustering the BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md).  
  
### Creating Domain Groups and Accounts  
 You need to configure the following domain groups and accounts before clustering the master secret server:  
  
-   Create domain groups with the names SSO Administrators and SSO Affiliate Administrators. To create a clustered instance of the Enterprise SSO service, you must create the SSO Administrators and SSO Affiliate Administrators groups as domain groups.  
  
-   Create or designate a domain account that is a member of the SSO Administrators domain group. The Enterprise SSO service on each node will be configured to log on as this domain account. This account must have the "Log on as a service" right on each node in the cluster. This account must also be granted Full Control access to the cluster.  
  
## Clustering the Master Secret Server  
 Here are the basic steps for clustering the master secret server:  
  
1. Install and configure Enterprise SSO on the cluster nodes.  
  
2. Create the clustered Enterprise SSO resource and the dependent resources.  
  
3. Restore the master secret on the second cluster node. If you move the master secret server to the cluster, you must restore the master secret on the first cluster node as well.  
  
4. Bring the cluster group that contains the SSO service, online.  
  
5. Update the master secret name in the Management database.  
  
   For detailed steps on clustering the master secret server, see [How to Cluster the Master Secret Server](http://go.microsoft.com/fwlink/?LinkId=156839) (<http://go.microsoft.com/fwlink/?LinkId=156839>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
## See Also  
 [Designating a New Master Secret Server Manually](../technical-guides/designating-a-new-master-secret-server-manually.md)