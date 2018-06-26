---
title: "High Availability for BizTalk Hosts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3153f7f7-7e82-4b0c-9b48-e9f871de285d
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# High Availability for BizTalk Hosts
BizTalk Server provides great flexibility in addressing high availability because you can strategically dedicate logical hosts to run specific areas of functionality, such as receiving and sending messages or processing orchestrations, that can be physically deployed to multiple servers.  
  
 A BizTalk Host is a logical container within a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group that can house [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] items such as adapter send handlers (including pipelines), receive locations, and orchestrations. You typically group items that have similar scale properties into a particular host.  
  
 After you create a host, you can deploy it to a physical [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer as a host instance. A host instance runs as a Windows service, BTSNTSvc.exe (or BTSNTSvc64.exe for 64-bit host instance), on the designated [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer. For each host, you can have only one instance on a particular [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer. However, you can have instances of a particular host on one or more [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers, and you can have instances of different hosts on a particular [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.  
  
 Items that are contained in BizTalk Hosts can perform the following functions:  
  
- **Receiving**. These items do the initial processing of messages after they are picked up in a receive location. When a host contains a receiving item, such as a receive location (with a pipeline), the message decoding and decrypting occurs in a pipeline within the host.  
  
- **Sending**. These items do the final processing of messages before they are sent out to the send port. When a host contains a sending item, such as a send port, the message signing and encryption occurs in a pipeline within the host.  
  
- **Processing**. These items process messages based on the instructions in orchestrations.  
  
  One BizTalk Host can contain items that receive, send, and process messages. For easier management and scalability, we recommend that you create different hosts designated for each function. In particular, we recommend that you use different hosts for processing and for receive/send operations.  
  
  For example, if you receive one message, run an orchestration, and send ten messages, you want to separate the receive and send functionality into two separate hosts because the send items will have ten times more traffic than the receive items. If you receive one message, run an orchestration, and send one message, you can think of these items as a unit of work and group them into one single host. Alternatively, you can separate them into three different hosts to increase performance and flexibility, although this also increases the management cost.  
  
  BizTalk Hosts are one of two types, *In-process* or *Isolated*. In-process hosts run inside of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime process (BTSNTSvc.exe  or BTSNTSvc64.exe) and Isolated hosts do not run in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime process. Isolated hosts are only used on the receiving side for the isolated receive adapters. The following table lists the items that each of these host types may contain.  
  
|Host type|Logical container for|  
|---------------|---------------------------|  
|In-process|-   Orchestrations<br />-   Adapter send handlers<br />-   In-process adapter receive handlers|  
|Isolated|-   HTTP, SOAP receive handlers<br />-   Any other isolated adapter receive handlers|  
  
 For more information about managing BizTalk Hosts and host instances, see [Managing BizTalk Hosts and Host Instances](http://go.microsoft.com/fwlink/?LinkID=154191) (http://go.microsoft.com/fwlink/?LinkID=154191) in BizTalk Server Help.  
  
 To provide high availability for BizTalk Hosts, you must have two or more host instances for each host (on two or more computers) in your environment. By having more than one host instance for each host you make sure that if one host instance becomes unavailable, the host instances on other computers that are running instances of the same host can resume the functions of the problematic or failed host instance, and that the overall system can continue performing with minimal disruption.  
  
## Disadvantages of Additional Hosts  
 While there are benefits of creating additional host instances, there are also potential drawbacks if too many host instances are created. Each host instance is a Windows service (BTSNTSvc.exe or BTSNTSvc64.exe), which generates additional load against the MessageBox database and consumes computer resources, such as CPU, memory, and threads. Other than these, you have the following reasons for not configuring too many additional host instances:  
  
-   Several performance counters are reported per host with too much granularity. This affects the usability for the administrator who would need to traverse through a lot of data. This has a negative impact on the overall view the administrator has.  
  
-   Each host consumes considerable amount of memory that might lead to a situation of throttling and reduced performance.  
  
-   If the hosts have receive adapters that continuously perform polling, each host will poll the database at short intervals, thereby resulting in degraded performance.  
  
## In This Section  
  
-   [Scaling Out Receiving Hosts](../technical-guides/scaling-out-receiving-hosts.md)  
  
-   [Clustering Receiving Hosts](../technical-guides/clustering-receiving-hosts.md)  
  
-   [Scaling Out Processing Hosts](../technical-guides/scaling-out-processing-hosts.md)  
  
-   [Scaling Out Sending Hosts](../technical-guides/scaling-out-sending-hosts.md)  
  
## See Also  
 [Configuring Hosts and Host Instances](../technical-guides/configuring-hosts-and-host-instances.md)   
 [Configuring a Dedicated Tracking Host](../technical-guides/configuring-a-dedicated-tracking-host.md)   
 [Planning for High Availability2](../technical-guides/planning-for-high-availability2.md)   
 [High Availability for Databases](../technical-guides/high-availability-for-databases.md)   
 [High Availability for the Master Secret Server](../technical-guides/high-availability-for-the-master-secret-server.md)