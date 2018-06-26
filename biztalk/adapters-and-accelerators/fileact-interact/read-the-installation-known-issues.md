---
title: "Read the installation known issues | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 245379f2-4048-4803-83ea-38dc23eb1a81
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Read the installation known issues
[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] have known issues listed in the following sections.  
  
## SWIFT Does Not Support Stress Testing on Integration Test Bed (ITB) and SWIFTNet Stub Environment  
 The ITB does not provide Service Level Agreement (SLA) in terms of throughput, and cannot guarantee that data is completely transmitted or consistent. You should stress test your implementation on the production network in the Pilot environment.  
  
 Additionally, you must ensure that all of the nodes (server, lines, and bandwidth) are properly configured to avoid any data loss. Following are typical sample throughputs:  
  
- Interact/Fileact Send under stressed computer: 20 messages/minute  
  
- Interact/Fileact Receive under stressed computer: 300-400 messages/minute  
  
  For more information, see your SWIFT documentation.  
  
## Messages Not Pushed When Queue Is Open  
 When you are using InterAct or FileAct Store and Forward (SnF) mode, if the session with the queue is open and messages are not being pushed, then you must restart SNLreceiver.exe. This avoids an issue with SWIFT that can occur occasionally.  
  
## You Must Use CDATA when Passing Characters like "<" and "&" in message  
 The term CDATA is used about text data that should not be parsed by the XML parser.  Characters like "<" and "&" are illegal in XML elements. "<" will generate an error because the parser interprets it as the start of a new element. "&" will generate an error because the parser interprets it as the start of a character entity. Everything inside a CDATA section is ignored by the parser. A CDATA section starts with "\<![CDATA[" and ends with "]]\>"  
  
## You Must Use Passthrough Pipelines with Payload-Only Mode  
 If you are using payload-only mode for the InterAct adapter, you must use pass-through pipelines on both the send and receive ports if you are not using custom pipelines.  
  
## Multiple Security Contexts Not Created (SWIFTNet Stub Computer)  
 On a SWIFTNet stub computer, multiple security contexts are not created for different send ports. Multiple security contexts are created on ITB.