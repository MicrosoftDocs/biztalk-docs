---
title: "What Is the WCF-NetNamedPipe Adapter? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF-NetNamedPipe adapters, about WCF-NetNamedPipe adapters"
ms.assetid: b9f84256-e49d-4ee2-b0fa-d3f692ade1d4
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the WCF-NetNamedPipe Adapter?
The WCF-NetNamedPipe adapter provides cross-process communication on the same computer in an environment in which both services and clients are WCF based. It provides full access to SOAP reliability and transaction features. The adapter uses the named pipe transport, and messages have binary encoding. This adapter cannot be used in cross-computer communication.  
  
 The following table summarizes the characteristics for the WCF-NetNamedPipe adapter.  
  
|Description|Characteristic|  
|-----------------|--------------------|  
|Interoperability level|.NET-Profile|  
|Message encoding|Binary|  
|Boundary|Cross-process|  
|Transport protocol|Named pipe|  
|Security mode|None and Transport|  
|Client authentication mechanism|Transport Security and Message Security|  
|Support for WS-ReliableMessaging|No|  
|Support for WS-AtomicTransaction|Yes|  
|Support for one-way messaging|Yes|  
|Support for two-way messaging|Yes|  
|Host type for receive adapter|In-process|  
|Host type for send adapter|In-process|  
  
 The WCF-NetNamedPipe adapter consists of two adapters—a receive adapter and a send adapter.  
  
 **WCF-NetNamedPipe Receive Adapter**  
  
 You use the WCF-NetNamedPipe receive adapter to receive WCF service requests over the named pipe transport. A receive location that uses the WCF-NetNamedPipe receive adapter can be configured as one-way or request-response (two-way).  
  
 **WCF-NetNamedPipe Send Adapter**  
  
 You use the WCF-NetNamedPipe send adapter to call a WCF service through the typeless contract over the named pipe transport.  
  
 For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).  
  
## See Also  
 [Configuring the WCF-NetNamedPipe Adapter](../core/configuring-the-wcf-netnamedpipe-adapter.md)   
 [WCF Adapters](../core/wcf-adapters.md)