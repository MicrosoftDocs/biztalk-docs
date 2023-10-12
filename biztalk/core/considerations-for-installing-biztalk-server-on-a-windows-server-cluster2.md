---
description: "Learn more about: Considerations for Installing BizTalk Server on a Windows Server Cluster"
title: "Considerations for Installing BizTalk Server on a Windows Server Cluster2"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Considerations for Installing BizTalk Server on a Windows Server Cluster
Special considerations must be made when installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a Windows Server cluster. This topic lists these considerations.

## A non-clustered BizTalk host instance should not be run on a Windows Server cluster where the Enterprise SSO service is clustered
 It is a recommended practice to cluster the Enterprise Single Sign-On Master Secret Server in an active/passive configuration to provide high availability for the master secret server. If a non-clustered BizTalk host instance and a clustered instance of the Enterprise SSO service are running on the same cluster node, the BizTalk host instance will fail if the clustered Enterprise SSO service is moved to a different node in the cluster. BizTalk Hosts maintain a dependency on a locally running instance of the Enterprise SSO service. Therefore if the Enterprise SSO service is configured as a clustered resource, then any BizTalk Hosts running on the cluster nodes must be configured as a clustered resource in the same cluster group.

## Configure the Microsoft Distributed Transaction Coordinator (MSDTC) as a clustered resource before installing BizTalk Server on a cluster
 If you plan to install BizTalk Server on a Windows Server cluster, you must cluster the Microsoft Distributed Transaction Coordinator first.

 To cluster MSDTC on a Windows Server 2008 failover cluster, follow the steps outlined in [Checklist: Creating an MS DTC Resource in a Windows Server 2008 Failover Cluster](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725955(v=ws.10))

## Network DTC access must be enabled on all BizTalk Servers and on the SQL Server before installing or configuring BizTalk Server
 To enable network DTC access on each cluster node as well as on the SQL Server that will host the BizTalk Server databases, follow the steps outlined in [How to Enable MSDTC on a Web Server](/previous-versions/commerce-server/dd327979(v=cs.90)) (<https://go.microsoft.com/fwlink/?LinkId=189701>). Network DTC access must be enabled to accommodate transactional support for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. We recommend that you restart each server after completing the steps in this Knowledge Base article.

## You must manually create domain groups in Active Directory before you configure BizTalk Server
 If you install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on multiple computers, you must specify domain groups and user accounts in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard. If you use domain groups for your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration, you must manually create the groups before you configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].