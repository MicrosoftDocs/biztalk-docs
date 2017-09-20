---
title: "SWIFT Send Adapter Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e52a5a21-0aa1-4cd9-a2a4-f9df425913a0
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Send Adapter Architecture
In general, BizTalk Server send adapters are hosted in the BizTalk service process, Btsntsvc.exe. This means that BizTalk Server manages the lifetime of the adapter.  
  
 There are two ways of sending messages to the SWIFT network: synchronous (ExchangeRequest) and asynchronous (not implemented for this release). In BizTalk Server, the send adapter should support the following communication patterns to interact with the BizTalk Messaging Engine:  
  
-   Solicit response — messages are exchanged in pairs, called the primitives, with the SWIFT network. Any messages sent to SWIFT will have a response be it business, acknowledgement or error. The response message is submitted back to messagebox. This mode of operation is used for Real-Time communication.  
  
-   One way send — the adapter when configured in one way operates in store and forward mode. The messages are sent to a preconfigured queue as opposed to a receipient. The sender can retrieve the response by opening a session with the queue in push or pull mode.  
  
> [!NOTE]
>  The way you create the adapter affects the way it operates.  
  
## In This Section  
  
-   [SWIFT Send Adapter URI](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-uri.md)  
  
-   [SWIFT Send Adapter Dynamic Send](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-dynamic-send.md)  
  
-   [SWIFT Send Adapter Initialization](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-initialization.md)  
  
-   [SWIFT Send Adapter Synchronous Mode](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-synchronous-mode.md)  
  
-   [SWIFT Send Adapter Termination](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-termination.md)