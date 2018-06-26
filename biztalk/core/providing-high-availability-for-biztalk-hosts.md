---
title: "Providing High Availability for BizTalk Hosts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, MessageBox database"
  - "planning, hosts"
  - "hosts, high availability"
  - "messages, routing"
  - "deploying, high availability"
  - "high availability, hosts"
  - "hosts"
  - "hosts, planning"
  - "MessageBox database"
ms.assetid: 9583b85c-7cad-4016-8065-5ca7de3f4359
caps.latest.revision: 47
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Providing High Availability for BizTalk Hosts
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides great flexibility for addressing high availability because you can strategically dedicate logical hosts to run specific areas of functionality such as receiving messages, sending messages or processing orchestrations.  
  
 A BizTalk host is a logical container within a BizTalk Server group that can house BizTalk Server items such as adapter handlers, receive locations (including pipelines), and orchestrations. You typically group items that have similar scaling requirements into a particular host. For example, you would group receive locations into a “receive” host, send ports into a “send” host, and orchestrations into an “processing” host.  
  
 After you create a host (a logical container), you can configure instances of the host to run on physical [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group. A host instance runs as a Windows Service on the designated [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer(s). Although it is not possible to run multiple instances of the same host on a given [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, you can run multiple instances of a particular host by configuring instances of the host on separate [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group. You can also run multiple instances of different hosts on a single [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.  
  
 Items that are contained in BizTalk hosts can perform the following functions:  
  
- **Receiving** These items do the initial processing of messages after they are picked up in a receive location. When a host contains a receiving item, such as a receive location or pipeline, it acts as a security boundary, and the message decoding and decrypting occurs in a pipeline within the host.  
  
- **Sending** These items do the final processing of messages before they are sent out to the send port. When a host contains a sending item, such as a send port or pipeline, the host acts as a security boundary, and the message signing and encryption occurs in a pipeline within the host.  
  
- **Processing** These items process messages based on the instructions in an orchestration.  
  
  Although a single BizTalk Host can contain items that receive, send, and process messages, it is considered a best practice to create different hosts for each function to create security boundaries and for easier management and scalability. In particular, we recommend that you use different hosts for processing and for receive/send operations, and that you separate trusted and non-trusted items.  
  
  For example, if you receive one message, run an orchestration, and send ten messages, you want to separate the receive and send functionality into two separate hosts because the send items will have ten times more traffic than the receive items. If you receive one message, run an orchestration, and send one message, you can think of these items as a unit of work and group them into one single host. Alternatively, you can separate them into three different hosts to increase performance and flexibility.  
  
  BizTalk hosts are one of two types, **In-process** or **Isolated**. In-process hosts run inside of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime process whereas Isolated hosts do not run in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime process. The following table lists the items that each of these host types may contain.  
  
|**Host Type**|**Logical container for**|  
|-------------------|-------------------------------|  
|In-Process|-   Orchestrations<br />-   Adapter Send Handlers<br />-   Adapter Receive Handlers other than HTTP and SOAP|  
|Isolated|HTTP and SOAP Receive Handlers|  
  
 For more information about hosts and host instances, see [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md).  
  
 To provide high availability for BizTalk hosts, you must have two or more host instances for each host in your environment (on two or more [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers). By having more than one host instance for each host you ensure that if one host instance becomes unavailable, the other computers that are running instances of that host can resume the functions of the problematic or failed host instance, and that the overall system can continue performing with minimal disruption.  
  
## Message Persistence  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] relies heavily on [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] for high availability because every host involved in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] persists messages to the BizTalk MessageBox database. For example, when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an incoming message, the receive host persists it to the MessageBox database before other hosts retrieve the message for orchestration processing and sending.  
  
 If your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution involves orchestration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] routes the message to the host that executes the business process (processing host), and saves the message to the MessageBox database after the orchestration finishes. The sending host then retrieves the message from the MessageBox database before sending it to the external application through the appropriate send adapter.  
  
## Separating the Host and Database Functions  
 Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] separates the data from the hosts that process the data, one step that you can take to create a highly available environment is to separate the host functions (sending, receiving, and processing) that occur in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] from the database functions that occur in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. By separating these functions, you can independently scale the processing, sending, and receiving hosts and the databases that store the data. The runtime and database layers are related, that is, if you increase the number of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers you will likely need to increase the number of computers that are running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] to handle the additional load. However, there is no direct relationship between the database layer and the BizTalk layer. They are two independent layers and you can scale them out separately.  
  
 What you must do to make the hosts highly available is different from what you must do to make the databases highly available. The following sections explain what you must do to make the receiving, sending, and processing hosts highly available. For more information about how to make the database layer highly available, see [Providing High Availability for BizTalk Server Databases](../core/providing-high-availability-for-biztalk-server-databases.md).  
  
 For deployments where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes more than SQL Server processes, you can configure multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers that use the same computer that is running SQL Server. This configuration uses the resources available on each computer. For example, if CPU or memory use runs high (more than 75 percent) on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer but runs low (less than 25 percent) on the computer that is running SQL Server, you can include additional [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers to distribute the workload while raising the resource utilization on the computer that is running SQL Server.  
  
## In This Section  
  
-   [Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md)  
  
-   [Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md)  
  
-   [Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md)  
  
-   [Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)  
  
## See Also  
 [Providing High Availability for BizTalk Server Databases](../core/providing-high-availability-for-biztalk-server-databases.md)   
 [High Availability for Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md)