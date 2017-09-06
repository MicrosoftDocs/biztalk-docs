---
title: "Transactional Message Batches | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1790c05-e3f7-4667-8a9e-f6f208e55e40
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transactional Message Batches
Some adapters must coordinate an external transaction with an internal [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] transaction. For example, the SQL adapter supplied with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must coordinate a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] transaction with a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] transaction. To do this, the adapter needs access to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] transaction object. A transaction object is explicitly created and associated with the batch before the batch is submitted to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. A batch that has an associated transaction object is called a transactional batch. By supplying your own Microsoft Distributed Transaction Coordinator (MSDTC) transaction object, you can achieve the "guaranteed, once and once only", delivery of data into and out of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Transactional database adapters like the SQL adapter have the potential for deadlocks in the external database because of the single transaction used for the batch. This is why the batch size for the SQL adapter is hard-coded to one.  
  
 Should the adapter need to enlist additional resource managers, such as another database or MSMQ, within the scope of that transaction, it must create and pass to the Messaging Engine an explicit external transaction. Creating an external transaction and associating it with a batch is a called a transactional batch. A transactional adapter is an adapter that makes use of transactional batches by explicitly creating an external Microsoft Distributed Transaction Coordinator (MSDTC) transaction.  
  
 One of the reasons an adapter provides [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with a transaction is to ensure that either [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or the external system has a record of the data. This record ensures the message is delivered once and only once.  
  
> [!NOTE]
>  For more information about MSDTC, see the documentation for the Distributed Transaction Coordinator at: [http://go.microsoft.com/fwlink/?LinkId=44297](http://go.microsoft.com/fwlink/?LinkId=44297).  
  
 The File adapter is an example of an adapter that does not require access to the transaction because the external file operations it manages are not transactional. In this case, the adapter does not provide a transaction object to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The SQL adapter, on the other hand, interacts with an SQL database and may have additional operations outside of its [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message interactions. An external MSDTC transaction in this case may make sense for the adapter to pass to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## In This Section  
  
-   [Handling Transactions](../core/handling-transactions.md)