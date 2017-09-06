---
title: "MQSeries Adapter Batching and Transaction Handling | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IBM WebSphere MQ queues"
  - "transactions, MQSeries adapters"
  - "MQSeries adapters, transactions"
  - "MQSeries adapters, IBM WebSphere MQ queues"
  - "MQSeries adapters, batching"
  - "batching, MQSeries adapters"
ms.assetid: 2e43fca9-acbd-4fd3-8df3-5f7398553830
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSeries Adapter Batching and Transaction Handling
The MQSeries adapter stops a transaction only if it does not receive all the data. The boundaries of a transaction for the adapter are the adapter endpoint (MQSeries queue on the MQSeries Server) and the MessageBox database.  
  
 If the BizTalk application invalidates a message, the adapter moves the message to the suspended queue. However, because it is still a valid transaction from the point of view of the adapter (the adapter received all the data), the adapter commits the transaction.  
  
 You can control batching and transaction handling by setting properties when configuring the adapter. For more information, see [Configuring the MQSeries Adapter](../core/configuring-the-mqseries-adapter.md).  
  
## See Also  
 [MQSeries Adapter Properties](../core/mqseries-adapter-properties.md)