---
title: "What Is the WCF-NetTcp Adapter? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF-NetTcp adapters, about WCF-NetTcp adapters"
ms.assetid: 94dc24df-19a1-4701-9012-59d05b0c8abd
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the WCF-NetTcp Adapter?
The WCF-NetTcp adapter provides connected cross-computer or cross-process communication in an environment in which both services and clients are WCF based. It provides full access to SOAP security, reliability, and transaction features. This adapter uses the TCP transport, and messages have binary encoding.  
  
 The following table summarizes the characteristics of the WCF-NetTcp adapter.  
  
|Description|Characteristic|  
|-----------------|--------------------|  
|Interoperability level|.NET-Profile|  
|Message encoding|Binary|  
|Boundary|Cross-computer or cross-process|  
|Transport protocol|TCP|  
|Security mode|None, Message, Transport, and TransportWithMessageCredential.|  
|Client authentication mechanism|Transport Security and Message Security|  
|Support for WS-ReliableMessaging|No|  
|Support for WS-AtomicTransaction|Yes|  
|Support for one-way messaging|Yes|  
|Support for two-way messaging|Yes|  
|Host type for receive adapter|In-process|  
|Host type for send adapter|In-process|  
  
 The WCF-NetTcp adapter consists of two adapters—a receive adapter and a send adapter.  
  
 **WCF-NetTcp Receive Adapter**  
  
 You use the WCF-NetTcp receive adapter to receive WCF service requests through the TCP protocol. A receive location that uses the WCF-NetTcp receive adapter can be configured as one-way or request-response (two-way).  
  
 **WCF-NetTcp Send Adapter**  
  
 You use the WCF-NetTcp send adapter to call a WCF service through the typeless contract by using the TCP protocol.  
  
 For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).  
  
## See Also  
 [Configuring the WCF-NetTcp Adapter](../core/configuring-the-wcf-nettcp-adapter.md)   
 [WCF Adapters](../core/wcf-adapters.md)