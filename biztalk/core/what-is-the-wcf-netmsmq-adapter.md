---
title: "What Is the WCF-NetMsmq Adapter? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF-NetMsmq adapters, about WCF-NetMsmq adapters"
ms.assetid: 506c5e2d-6cbe-4788-8e37-49d009dc559a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the WCF-NetMsmq Adapter?
The WCF-NetMsmq adapter provides disconnected cross-computer communication by using queuing technology in an environment where both the services and clients are WCF based. It uses the Message Queuing (MSMQ) transport, and messages have binary encoding.  
  
 The following table summarizes the characteristics for the WCF-NetMsmq adapter.  
  
|Description|Characteristic|  
|-----------------|--------------------|  
|Interoperability level|.NET-Profile|  
|Message encoding|Binary|  
|Boundary|Cross-computer|  
|Transport protocol|MSMQ|  
|Security mode|None, Message, Transport, and Both.|  
|Client authentication mechanism|Transport Security and Message Security|  
|Support for WS-ReliableMessaging|Not applicable|  
|Support for WS-AtomicTransaction|Yes|  
|Support for one-way messaging|Yes|  
|Support for two-way messaging|No|  
|Host type for receive adapter|In-process|  
|Host type for send adapter|In-process|  
  
> [!NOTE]
>  The queues from which the WCF-NetMsmq receive adapter pulls messages must be created in advance. The messages in the queues must be WCF based; otherwise, these messages will be sent to the dead-letter queue.  
  
 The WCF-NetMsmq adapter consists of two adapters—a receive adapter and a send adapter.  
  
 **WCF-NetMsmq Receive Adapter**  
  
 You use the WCF-NetMsmq receive adapter to receive WCF service requests over MSMQ. A receive location that uses the WCF-NetMsmq receive adapter can only be configured as one-way receive.  
  
 **WCF-NetMsmq Send Adapter**  
  
 You use the WCF-NetMsmq send adapter to call a WCF service through the typeless contract over MSMQ.  
  
 For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).  
  
## See Also  
 [Configuring the WCF-NetMsmq Adapter](../core/configuring-the-wcf-netmsmq-adapter.md)   
 [WCF Adapters](../core/wcf-adapters.md)