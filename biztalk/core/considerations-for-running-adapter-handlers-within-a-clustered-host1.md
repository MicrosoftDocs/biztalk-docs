---
title: "Considerations for Running Adapter Handlers within a Clustered Host1 | Microsoft Docs"
ms.custom: ""
ms.date: "2016-03-17"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "high availability"
  - "receive adapters, clustering"
  - "clustering, POP3 adapters"
  - "FTP adapters, clustering"
  - "clustering, receive adapters"
  - "NLB system"
  - "MSMQ send handler"
  - "MSMQ receive handler"
  - "clustering, FTP adapters"
  - "handlers [adapters], best practices"
  - "hosts, clustering"
  - "MSMQ adapters"
  - "clustering, MSMQ adapters"
  - "adapters, best practices"
  - "adapters, handlers"
  - "POP3 adapters, clustering"
  - "MSMQ adapters, clustering"
  - "clustering"
ms.assetid: ee66663c-4f4d-4515-9df1-aacf4fc72be4
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations for Running Adapter Handlers within a Clustered Host
BizTalk host cluster support is available to provide high availability for the following integrated BizTalk adapters: the FTP adapter, the SFTP adapter, the MSMQ adapter, and the POP3 adapter. Host cluster support is also provided so that there is high availability for running a single instance of an adapter for purposes of ordered delivery.  
  
 All of the BizTalk adapter handlers  can be run in a clustered host but there is no benefit derived for running adapter handlers in a clustered host except as described below. If your processing requirements do not include any of the scenarios described below, then you should not run adapter handlers in a clustered host.  
  
## Running the FTP or SFTP adapter receive handler within a clustered BizTalk host  
 For most of the BizTalk Server integrated adapters, high availability can be achieved by creating multiple adapter handlers to run on BizTalk host instances on different [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] servers within a BizTalk group. FTP or SFTP adapter receive handlers should not, however, be configured to run in multiple BizTalk host instances simultaneously. This recommendation is made because the FTP or SFTP receive adapter uses the FTP or SFTP protocol to retrieve files from the target system. The FTP or SFTP protocol does not lock files to ensure that multiple copies of the same file are not retrieved simultaneously when running multiple instances of the FTP or SFTP receive adapter.  
  
 To provide high availability for the FTP or SFTP receive adapter, you should configure the FTP or SFTP receive adapter to run in a BizTalk host instance that has been clustered.  
  
## Running MSMQ adapter handlers within a clustered BizTalk host  
 To ensure high availability for the MSMQ adapter and to ensure transactional consistency for messages sent or received by the MSMQ adapter, you should do the following:  
  
1. Configure Message Queuing (MSMQ) as a clustered resource in a Windows cluster group on your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers.  
  
2. Add the clustered MSMQ service to the list of Resource dependencies for the clustered BizTalk host. This ensures that the clustered BizTalk host always starts after the clustered MSMQ service in failover scenarios.  
  
3. Configure the MSMQ adapter send and receive handlers in a BizTalk host instance that has been configured as a cluster resource in the same cluster group as the clustered MSMQ resource.  
  
   These steps are recommended for the following reasons:  
  
   **MSMQ adapter receive handler** – MSMQ versions prior to MSMQ 4.0 (Windows Server 2008) do not support remote transactional reads; only local transactional reads are supported. In this case, the MSMQ adapter receive handler must run in a host instance that is local to the clustered Message Queuing service to complete local transactional reads with the MSMQ adapter.  
  
> [!IMPORTANT]
>  The MSMQ adapter receive handler requires that a local non-clustered instance of the Message Queuing service is running on the same computer that the receive handler host instance is running on.  
  
 **MSMQ adapter send handler** - To ensure the consistency of transactional sends made by the MSMQ adapter, the outgoing queue used by the MSMQ adapter send handler should be highly available so that if the MSMQ service for the outgoing queue fails it can be resumed. Configuring a clustered Message Queuingresource and the MSMQ adapter handlers in a cluster group will ensure that the outgoing queue used by the MSMQ adapter send handler will be highly available. This will mitigate the possibility of message loss in the event that the Message Queuing service fails.  
  
> [!NOTE]
>  If the MSMQ receive location is **only** receiving from MSMQ queues on a remote MSMQ server, then high availability can be achieved by running the MSMQ receive host on multiple BizTalk computers in the BizTalk group.  To provide high availability for MSMQ, you must ensure the remote MSMQ server is using failover clustering in Windows.  If using transactional queues, the remote MSMQ server must be running MSMQ 4.0 (Windows Server 2008) or above.  
  
## Running the POP3 adapter receive handler within a clustered BizTalk host  
 The POP3 adapter receive handler does not need to be configured to run in a clustered BizTalk host unless the POP3 server that the adapter is reading from allows multiple concurrent connections to be made to the same mailbox. If the POP3 server that the POP3 adapter is connected to permits multiple concurrent connections to its mailboxes, then we recommend that you ensure high availability for the POP3 adapter by configuring a single POP3 adapter receive handler to run in a BizTalk host instance that has been clustered. This recommendation is made to ensure that multiple copies of the same e-mail message are not retrieved simultaneously when running multiple instances of the POP3 receive adapter.  
  
## Running a receive adapter that supports ordered delivery with a clustered BizTalk host  
 The MSMQ and MQSeries integrated adapters provide the ability to submit documents to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the order that they were received. Correct implementation of this functionality requires that only a single instance of these receive adapters be running at any given time. To provide high availability for a single instance of these adapters, they should be configured to run in a clustered BizTalk host instance.