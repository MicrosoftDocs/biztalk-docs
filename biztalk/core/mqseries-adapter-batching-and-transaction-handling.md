---
description: "Learn more about: MQSeries Adapter Batching and Transaction Handling"
title: "MQSeries Adapter Batching and Transaction Handling"
ms.custom: "devx-track-javaee-websphere"
ms.date: "12/30/2022"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MQSeries Adapter Batching and Transaction Handling
The MQSeries adapter stops a transaction only if it does not receive all the data. The boundaries of a transaction for the adapter are the adapter endpoint (MQSeries queue on the MQSeries Server) and the MessageBox database.  
  
 If the BizTalk application invalidates a message, the adapter moves the message to the suspended queue. However, because it is still a valid transaction from the point of view of the adapter (the adapter received all the data), the adapter commits the transaction.  
  
 You can control batching and transaction handling by setting properties when configuring the adapter. For more information, see [Configuring the MQSeries Adapter](../core/configuring-the-mqseries-adapter.md).  
  
## See Also  
 [MQSeries Adapter Properties](../core/mqseries-adapter-properties.md)
