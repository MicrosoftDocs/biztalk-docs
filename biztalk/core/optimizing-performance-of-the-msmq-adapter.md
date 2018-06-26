---
title: "Optimizing Performance of the MSMQ Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSMQ adapters, performance"
  - "performance, MSMQ adapters"
  - "configuring [MSMQ adapters], performance"
ms.assetid: f8537ea8-a96e-4874-bcaf-cd1442a50bd4
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Optimizing Performance of the MSMQ Adapter
Optimization of the MSMQ adapter differs between the send and receive sides. You control optimization on the receive side by setting a property on the receive location. On the send side, you can control optimization by using an orchestration.  
  
## Receive Optimization  
 On the receive side, you can have the adapter use a single execution thread. Whether the adapter uses a single thread or multiple threads depends on the setting of the **Ordered Processing** property on the receive location, as follows:  
  
- When the property is **True**, the adapter operates on a single thread. This limits the adapter to one message at a time and conserves memory. Notice that this effectively sets **Batch Size** to one (1), regardless of the value assigned to it in the property sheet.  
  
- When **Ordered Processing** is **False**, the adapter runs multiple threads and can process multiple messages at a time, therefore increasing performance.  
  
  You must set **Ordered Processing** to **True** if you put a premium on managing server resources, or if the number or size of messages might exhaust available memory.  
  
  You can also control memory use by reducing the value of **Batch Size** on the receive location. A smaller batch size keeps fewer messages in memory and therefore uses less memory.  
  
  Placing send ports and receive locations on separate computers can also reduce memory use.  
  
## Send Optimization  
 On the send side, you can achieve the equivalent single-message processing by using the sample orchestration. The sample sends a single message and then waits to send the next message until it receives an acknowledgment. For more information, see [How to Create MSMQ Receive Locations and Send Ports from Code](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md).  
  
## Remote Transactional Read Operations  
 With BizTalk Server the MSMQ adapter is capable of making remote read operations from transactional MSMQ queues.  This is because MSMQ 4.0 and later versions support remote transactional read operations.  However, transactional read operations are typically slow operations. To optimize performance they should be used only when there is no other option.  
  
## See Also  
 [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md)   
 [How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md)   
 [Configuring the MSMQ Adapter](../core/configuring-the-msmq-adapter.md)