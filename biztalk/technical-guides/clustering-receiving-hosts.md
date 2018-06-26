---
title: "Clustering Receiving Hosts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93544f39-836f-4a4f-9587-230bfa3a9d4e
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Clustering Receiving Hosts
BizTalk Server provides functionality that allows you to configure a BizTalk Host as a clustered resource within a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster group. Host cluster support is provided to support high availability for integrated BizTalk receive adapters that should not be run in multiple host instances simultaneously, such as the FTP receive handler or, under certain circumstances, the POP3 receive handler. Host cluster support is also provided to ensure transactional consistency for messages sent or received by the MSMQ adapter in scenarios that require that the MSMQ service is clustered.  
  
> [!NOTE]
>  Host clustering is available only with BizTalk Server Enterprise Edition.  
> 
> [!NOTE]
>  Before you can cluster a BizTalk Host you must have configured at least two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in a BizTalk group as members of a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster. For more information about configuring a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster, see [Windows Server 2008 Clustering Documents, Whitepapers, Webcasts, Groups](http://go.microsoft.com/fwlink/?LinkId=156818) (<http://go.microsoft.com/fwlink/?LinkId=156818>).  
  
 BizTalk Host cluster support is available to provide high availability for five of the integrated BizTalk adapters: the FTP adapter, the MSMQ adapter, the POP3 adapter, the SQL adapter, and the SAP adapter. Host cluster support is also provided so that there is high availability for running a single instance of an adapter for purposes of ordered delivery.  
  
 All of the BizTalk adapter handlers can be run in a clustered host, but there is no benefit from running adapter handlers in a clustered host except as described below. If your processing requirements include any of the scenarios described in the section below, then you should run adapter handlers in a clustered host. For detailed steps of setting up [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] clusters, see [Improving Fault Tolerance in BizTalk Server by Using a Windows Server 2008 Failover Cluster or Windows Server 2003 Server Cluster](http://go.microsoft.com/fwlink/?LinkId=156819) (<http://go.microsoft.com/fwlink/?LinkId=156819>).  
  
## Scenarios for Running Adapter Handlers in Clustered Hosts  
 If your processing requirements include any of the scenarios listed below, then you should run adapter handlers in a clustered host.  
  
- Running the FTP adapter receive handler within a clustered BizTalk host  
  
- Running MSMQ adapter handlers within a clustered BizTalk host  
  
- Running the POP3 adapter receive handler within a clustered BizTalk host  
  
- Running a receive adapter that supports ordered delivery with a clustered BizTalk host  
  
  For more information about these scenarios, see [Considerations for Running Adapter Handlers within a Clustered Host](http://go.microsoft.com/fwlink/?LinkId=151284) (http://go.microsoft.com/fwlink/?LinkId=151284).  
  
## See Also  
 [Scaling Out Receiving Hosts](../technical-guides/scaling-out-receiving-hosts.md)   
 [Scaling Out Processing Hosts](../technical-guides/scaling-out-processing-hosts.md)   
 [Scaling Out Sending Hosts](../technical-guides/scaling-out-sending-hosts.md)