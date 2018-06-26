---
title: "Transaction Handling with the MSMQ Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSMQ adapters, transaction handling"
  - "transactions, MSMQ adapters"
ms.assetid: 2e5dd0da-3852-48bf-9372-b019ecab23be
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transaction Handling with the MSMQ Adapter
This section discusses how transactions work in receiving and sending.  
  
> [!NOTE]
>  For the MSMQ adapter, a transaction extends from the BizTalk MessageBox database to the local Message Queuing queue even if you are using a remote queue.  
  
 You can use transactions on both send and receive with the MSMQ adapter. On transacted sends, the adapter accumulates messages until it has a complete batch. The adapter then submits the batch to the local Message Queuing service as a single transaction. If the submission fails, the adapter tries to resubmit the batch. If the resubmission fails, the adapter moves to the secondary transport.  
  
> [!NOTE]
>  The adapter supports transactional reads of remote queues with Message Queuing 4.0 or later only. In this scenario both the BizTalk Server and the remote Message Queuing server must be running Message Queuing 4.0 or later.  
  
 On transacted receives, the adapter suspends failed messages so that it does not lose any one of the messages. During a transacted receive the adapter adds messages to a batch until the batch is complete. It then submits the batch:  
  
- If there are no problems and the server receives the messages, the adapter commits the transaction.  
  
- If there are problems, the adapter creates a new batch as part of the current transaction. It then moves any problem messages into the new batch. It then resubmits the first batch and submits the new batch as suspended messages. The adapter commits the transaction if there are no problems during this resubmission.  
  
  If you are running an MSMQ adapter send handler in a clustered BizTalk Host instance, you should cluster the MSMQ service in the same cluster group to ensure transactional consistency.  
  
  If "Network DTC Access" is disabled in the DCOMCNFG utility, a MSMQ transactional remote receive operation will fail with a cryptic error message.  To do a transactional remote receive with the MSMQ adapter, "Network DTC Access" must be enabled. More information can be found at [http://go.microsoft.com/fwlink/?LinkId=124623](http://go.microsoft.com/fwlink/?LinkId=124623).  
  
  If you are running an MSMQ adapter receive handler in a clustered BizTalk Host instance, you should cluster the MSMQ service in the same cluster group to support local transacted reads because MSMQ does not support remote transactional reads. For more information about running MSMQ adapter handlers in a clustered instance of a BizTalk Host, see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  
  
## See Also  
 [Reliable Messaging with the MSMQ Adapter](../core/reliable-messaging-with-the-msmq-adapter.md)