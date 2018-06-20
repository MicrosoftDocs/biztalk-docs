---
title: "Troubleshooting a Windows Server Cluster | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 283cf4cd-ce40-48b7-8549-9ab17d7d2c34
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting a Windows Server Cluster
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports the use of Windows Server cluster for host cluster support, to provide high availability for the Enterprise Single Sign-On (SSO) Master Secret, and to provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. This topic provides some general guidelines for using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a Windows Server cluster environment and discusses some known issues that may occur when using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a Windows Server cluster environment.  
  
## General Guidelines  
 Follow these general guidelines to maximize productivity with Windows Server cluster and to troubleshoot Windows Server cluster problems that may affect [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
1. Complete [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] proof of concept work with a Windows Server cluster in a virtualized server environment.  
  
    **The Hyper-V role available with Windows Server 2008 can be used to create a virtualized server environment.**  
  
   - For more information about Windows Server 2008 Hyper-V, see “Virtualization and Consolidation” at [http://go.microsoft.com/fwlink/?LinkID=121187](http://go.microsoft.com/fwlink/?LinkID=121187).  
  
   - For more in depth information about the benefits of leveraging virtualization technology provided with Hyper-V, see the whitepaper "Advanced Virtualization Benefits of Windows Server 2008 Editions for the Enterprise" available for download at [http://go.microsoft.com/fwlink/?LinkId=123530](http://go.microsoft.com/fwlink/?LinkId=123530).  
  
   - Steps for using Hyper-V to create a Windows Server 2008 cluster are available at [http://go.microsoft.com/fwlink/?LinkId=129680](http://go.microsoft.com/fwlink/?LinkId=129680).  
  
     Doing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] proof of concept work with a Windows Server cluster in a virtualized server environment offers great flexibility and uses considerably fewer hardware resources than required for a Windows Server cluster. If this approach is used, allocate at least 512 MB of memory for each virtual machine that is concurrently running on the host computer and an additional 512 MB of memory for the host operating system. For example, for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution with a Windows Server cluster that uses five virtual machines (two BizTalk Server cluster nodes, two Microsoft SQL Server cluster nodes, and one domain controller), you would plan to have 3 GB of memory installed on the host computer. If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] proof of concept environment requires more than 2 GB of memory, consider installing a 64-bit version of Windows on the host computer (required for the Hyper-V role) to ensure that all installed memory is accessible by the host operating system.  
  
## Troubleshooting Resources  
 **Resources for troubleshooting Windows Server 2008 failover clustering**  
  
-   Review the [Failover Cluster Validation and Troubleshooting with Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=129729) TechNet Webcast on the Microsoft TechNet Web site. This web cast describes how to troubleshoot failover cluster validation and troubleshooting with Windows Server 2008.  
  
-   For more information about analyzing problems with Windows Server 2008 failover clustering, review the topic [View Events and Logs for a Failover Cluster](http://go.microsoft.com/fwlink/?LinkId=129730) on the Microsoft TechNet Web site.  
  
## Known Issues  
  
#### Any attempt to bring a clustered MSDTC resource online fails which causes dependent BizTalk Server services to fail  
  
##### Problem  
 A clustered Distributed Transaction Coordinator (MSDTC) resource cannot be brought online through the **Bring Online** option in Cluster Administrator, which causes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time operations that are dependent upon MSDTC transaction support to fail.  
  
##### Cause  
 Clustered MSDTC resource failure can occur for a number of reasons including the following:  
  
-   The clustered MSDTC resource is not configured with the correct Disk and Network Name resource dependencies or the resource dependencies are failing.  
  
-   Permissions problems are preventing the clustered MSDTC resource from being activated.  
  
##### Resolution  
 **Complete the following steps on a Windows Server 2008 cluster:**  
  
-   Follow the steps in [Checklist: Creating an MS DTC Resource in a Windows Server 2008 Failover Cluster](http://go.microsoft.com/fwlink/?LinkId=129677) for creating one or more clustered MSDTC resources on a Windows Server 2008 failover cluster.  
  
## See Also  
 [Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [Clustering the BizTalk Server Databases](../core/clustering-the-biztalk-server-databases1.md)   
 [Sample BizTalk Server High Availability Scenarios](../core/sample-biztalk-server-high-availability-scenarios.md)   
 [High-Availability SSO Installation Options](../core/high-availability-sso-installation-options.md)