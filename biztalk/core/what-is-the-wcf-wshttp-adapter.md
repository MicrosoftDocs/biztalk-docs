---
description: "Learn more about: What Is the WCF-WSHttp Adapter?"
title: "What Is the WCF-WSHttp Adapter?"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# What Is the WCF-WSHttp Adapter?
You can use the WCF-WSHttp adapter to do cross-computer communication with services and clients that can understand the next-generation Web service standards, using either the HTTP or HTTPS transport with text or Message Transmission Optimization Mechanism (MTOM) encoding. The WCF-WSHttp adapter provides full access to the SOAP security, reliability, and transaction features.  
  
 The following table summarizes the characteristics of the WCF-WSHttp adapter.  
  
|Description|Characteristic|  
|-----------------|--------------------|  
|Interoperability level|WS-Profile|  
|Message encoding|Text or MTOM|  
|Boundary|Cross-computer|  
|Transport protocol|HTTP or HTTPS|  
|Security mode|None, Message, Transport, and TransportWithMessageCredential.|  
|Client authentication mechanism|Transport Security and Message Security|  
|Support for WS-ReliableMessaging|No|  
|Support for WS-AtomicTransaction|Yes|  
|Support for one-way messaging|Yes|  
|Support for two-way messaging|Yes|  
|Host type for receive adapter|Isolated|  
|Host type for send adapter|In-process|  
  
 The WCF-WSHttp adapter consists of two adapters—a receive adapter and a send adapter.  
  
 **WCF-WSHttp Receive Adapter**  
  
 You use the WCF-WSHttp receive adapter to receive WCF service requests through the HTTP or HTTPS protocol. A receive location that uses the WCF-WSHttp receive adapter can be configured as one-way or request-response (two-way).  
  
 **WCF-WSHttp Send Adapter**  
  
 You use the WCF-WSHttp send adapter to call a WCF service through the typeless contract by using the HTTP or HTTPS protocol.  
  
 For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).  
  
## See Also  
 [Configuring the WCF-WSHttp Adapter](../core/configuring-the-wcf-wshttp-adapter.md)   
 [WCF Adapters](../core/wcf-adapters.md)
