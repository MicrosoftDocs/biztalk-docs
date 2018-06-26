---
title: "How to Create a BizTalk Server Hosting Environment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "hosting environments, creating"
  - "managing [hosts], hosting environments"
  - "hosts, environments"
  - "managing [hosts], creating"
  - "creating, hosting environment"
ms.assetid: 6f335139-1121-45ff-88da-5c626b8fff97
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a BizTalk Server Hosting Environment
Before you create your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hosting environment, consider the following recommendations:  

- **Use different hosts for trusted and non-trusted orchestrations and receive handlers**  

   Any items running in a host (for example, orchestrations, pipelines, receive and send handlers) run under the same identity, and have access to the work and suspended queues for that host.  

   If a message cannot be delivered to an orchestration due to permission errors, the message is placed in the suspended queue of the host where the sending process (a receive pipeline or another orchestration) is running. However, if the orchestration and the sending process (for example, a receive pipeline) are running in the same host, the orchestration can still access the message in the suspended queue. This could potentially compromise your system if a non-trusted orchestration is running in a trusted host.  

   We recommend that you run non-trusted orchestrations in a separate host, with a different service account than the trusted hosts in your BizTalk group. For information about designating a host as trusted, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).  

- **Limit the database and log size in the BizTalk Server databases**  

   The BizTalk MessageBox databases and the BizTalk Tracking database grow much faster than the other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. As part of your backup and maintenance program, you should update these databases frequently.  

   By default, the tables in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases do not have a log size limit. As part of your backup and maintenance program, we recommend that you limit the log size to prevent the logs from becoming too large and potentially using all the disk space. For information about managing the size of tracking database, see [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md).  

- **Use SQL Server clustering**  

   To provide high availability of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, we recommend that you cluster the SQL servers where the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are stored. This will help minimize downtime if one of the databases or SQL Server fails. For more information about SQL Server clustering, see "Failover Clustering Architecture" in SQL Server Books Online.  

## Prerequisites  
 The following are prerequisites for performing the procedure in this topic:  

- You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

- The instructions in the following procedure assume that you have installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with the complete installation option. If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with the complete installation option, some of the administration objects listed in step 1 may not be on your system.  

### To create a BizTalk Server hosting environment  

1. Use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration to create a new BizTalk group. For information about creating a new [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group, see [Configuring Groups Using the BizTalk Server Configuration](http://msdn.microsoft.com/library/16beb7bb-091c-4056-8622-cc79c95186e9).  

    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration creates the following administration objects:  


   |                   Administration object                    |                                                                                                                                                                                                                                       Description                                                                                                                                                                                                                                       |
   |------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |      **BizTalk Management** database (BizTalkMgmtDb)       |                                                                                                                                                                    This database is the central meta-information store for all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s.                                                                                                                                                                     |
   |     **BizTalk MessageBox** database (BizTalkMsgBoxDb)      |           This database stores subscriptions predicates. It is a host platform, and keeps the queues and state tables for each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host. The MessageBox database also stores the messages and message properties. For information about MessageBox databases, including adding additional MessageBox databases, see [Managing MessageBox Databases](../core/managing-messagebox-databases.md).           |
   |                         **Server**                         | This is the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed and configured, and where host instances are running. You create host instances from a host created on a server. For more information about creating a host, see [How to Create a New Host](../core/how-to-create-a-new-host.md). For information about creating host instances, see [How to Add a Host Instance](../core/how-to-add-a-host-instance.md). |
   |     **BAM Primary Import** database (BAMPrimaryImport)     |                                                                                                                                                                                                This is the database where the Business Activity Monitoring tool collects tracking data.                                                                                                                                                                                                 |
   |       **Rule Engine** database (BizTalkRuleEngineDb)       |                                                                                                                                                                                       This database is a repository for policies, rules, and vocabularies for data references in business rules.                                                                                                                                                                                        |
   |        **BizTalk Tracking** database (BizTalkDTADb)        |                                                                                                                                                       This database stores business and health-monitoring data tracked by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tracking engine.                                                                                                                                                       |
   |                  **SSO** database (SSODB)                  |                                                                                                                                                                                                                      This database stores credential information.                                                                                                                                                                                                                       |
   |   **In-process host** with corresponding host instances    |                                                                                                                                                                        The in-process host operates within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process space.                                                                                                                                                                        |
   |    **Isolated host** with corresponding host instances     |                                                                                                                                                                       The isolated host operates outside of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.                                                                                                                                                                        |
   | HTTP/S, BizTalk Message Queuing, File, SMTP, SOAP, and SQL |                                                                                                                                                                   The Configuration Wizard creates the adapters that are part of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].                                                                                                                                                                    |


2. Use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or WMI to add components to your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment as needed. To scale out your solution, add MessageBox databases, hosts, and servers.  

3. Use the BizTalk Administration Console or WMI to create host instances on the mapped servers. This step determines on which servers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will run. As the needs in your enterprise change, you can add servers, remove servers, and change server-to-host mapping.  

## See Also  
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Hosts](../core/hosts.md)   
 [Host Instances](../core/host-instances.md)