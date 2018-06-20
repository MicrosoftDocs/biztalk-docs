---
title: "Difference between adapter channel and service in the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24d41d96-0ea1-4a97-bd45-b65afdbbd923
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Difference between adapter channel and service in the WCF LOB Adapter SDK
The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] each provide a set of APIs that can be used to expose application functionality to consuming applications on the same computer or across a network. To choose the most appropriate framework, you must consider the properties of the target system application you are exposing as well as the business requirements for the exposed functionality. This topic provides guidelines that you can use to choose the appropriate framework.  
  
## When to Write an Adapter  
 Consider writing an adapter using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] when:  
  
- The target system is an existing, non-*Web services-enabled* system  
  
- The target system is dynamic and can be enhanced with new operations  
  
- The target system has a large amount of metadata  
  
- There is a large, diverse number of users for the target system's data  
  
- Consuming applications need rich application metadata discovery functionality  
  
  For example, if the target system contains hundreds of operations for managing health care claims, and the operations are dynamic (meaning users can add new operations that perform additional tasks), it makes sense to expose this functionality using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. This will ensure that new operations are discoverable by applications using the adapter. With [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], you would have to modify the service contract because it is static.  
  
## When to Write a Service  
 Use the *WCF Service Model* to create a service when:  
  
- The target system is static and has a fixed set of operations  
  
- The target system has little or no metadata  
  
- Service developers have detailed knowledge of the application to be exposed  
  
- A brand new application is being exposed  
  
- You are creating generic transport adapters  
  
  For example, if the target system contains 20 operations for managing sports teams, you can expose the operations as a static contract using [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]. By doing so, you avoid implementing unnecessary metadata features and you can potentially minimize development time.  
  
## When to Write a Channel  
 Use the *WCF Channel Model* to create a channel when:  
  
-   Creating a wire protocol. Examples of wire protocols include WS-ReliableMessaging Protocol.  
  
-   Send/receive WCF messages over a transport other than ones that are included in WCF (TCP, HTTP, Named Pipes, MSMQ and PeerChannel). For example, you can write a UDP transport, TIBCO, or a Java Messaging Service (JMS) transport.  
  
-   Integrating with a system that is not exposed as a Web service.  In this case your transport acts as an adapter adapting WCF messages to the existing system's message format or API allowing a WCF client to talk directly to the existing system. An example of this is the Web Services Enhancement (WSE) 3.0 TCP transport.  
  
## See Also  
 [Plan and design an adapter using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)   
 [Understand the LOB system with the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md)