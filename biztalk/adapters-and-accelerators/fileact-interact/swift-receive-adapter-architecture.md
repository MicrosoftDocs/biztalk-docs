---
title: "SWIFT Receive Adapter Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16f32689-0b70-4389-8596-991fd776f185
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Receive Adapter Architecture
In BizTalk Server, the receive adapter is hosted within its own memory space, which means a separate process is created to run the host. This host is spawned by defining a subsystem in the SWIFTNet Link (SNL) configuration.  
  
 The server executable is configured as a subsystem in the SNL configuration (paramfile) and is spawned by executing the SWIFTNet Start command. The SNL server application is terminated by executing the SWIFTNet Stop command. SNL manages the lifetime of the server executable.  
  
> [!NOTE]
>  The service bureau scenario requires the adapter to service multiple SWIFT members running under their own security contexts. This can be supported by configuring an individual receive location per member and spawning multiple instances of the server executable — each one dedicated to one receive location.  
  
 In BizTalk Server, the receive adapter supports the following communication patterns to interact with the BizTalk Messaging Engine:  
  
-   One way — this mode is required when the receive adapter (server) is operating in deferred mode. In deferred mode, the adapter sends a default acknowledgment for incoming messages. The default values for the acknowledgment can be configured in the adapter properties. Business level response can be sent later by the LOB application through the send adapter.  
  
    > [!NOTE]
    >  In case of deferred mode, all values must be filled up in the adapter configuration, since the adapter is constructing the response.  
  
-   Request response — in this mode the adapter submits the request from SWIFT to BizTalk and waits for response. The adapter would timeout if there is no response from the LOB application. The time out value is configurable in adapter configuration. The default value is 60 seconds.  
  
     The receive adapter can receive the callback from SNL only on one thread. This means that the receive adapter can receive further messages from SNL only after submitting the first message. Therefore, the default batch size is set to 1.  
  
## In This Section  
  
-   [SWIFT Receive Adapter URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md)  
  
-   [SWIFT Receive Adapter Initialization](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md)  
  
-   [SWIFT Receive Adapter Security Context](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md)  
  
-   [SWIFT Receive Adapter Synchronous and Deferred Modes](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md)  
  
-   [SWIFT Receive Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)