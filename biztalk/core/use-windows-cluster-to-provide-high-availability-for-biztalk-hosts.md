---
title: "Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2 | Microsoft Docs"
ms.custom: ""
ms.date: "2016-01-04"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Passive configuration [Master Secret server]"
  - "Active configuration [Master Secret server]"
  - "clustering, about clustering"
  - "high availability"
  - "Windows Server cluster, warnings"
  - "installation, high availibility planning"
  - "Master Secret server"
  - "installation, configuring"
  - "Master Secret server, configuring"
  - "installation, Windows Server cluster"
  - "clustering"
ms.assetid: 4d7f0842-561e-49e0-ab08-504256b9294f
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides functionality that allows you to configure a BizTalk host as a clustered resource within a  Windows Server failover cluster group. Host cluster support is provided to support high availability for integrated BizTalk adapters that should not be run in multiple host instances simultaneously, such as the FTP receive handler or, under certain circumstances, the POP3 receive handler. Host cluster support is also provided to ensure transactional consistency for messages sent or received by the MSMQ adapter in scenarios that require that the MSMQ service is clustered.  
  
> [!NOTE]
>  Host clustering is only available with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Enterprise Edition.  
> 
> [!NOTE]
>  Before you can cluster a BizTalk host, you must have configured at least two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group as members of a Windows Server Failover cluster. For more information about configuring a Windows Server Failover cluster, please see the Windows Server online help.  
  
## In This Section  
  
-   [Considerations for Installing BizTalk Server on a Windows Server Cluster](../core/considerations-for-installing-biztalk-server-on-a-windows-server-cluster2.md)  
  
-   [How to Configure a BizTalk Host as a Cluster Resource](../core/how-to-configure-a-biztalk-host-as-a-cluster-resource1.md)  
  
-   [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)