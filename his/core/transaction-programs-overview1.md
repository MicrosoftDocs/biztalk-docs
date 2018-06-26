---
title: "Transaction Programs Overview1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5938167-41c9-4093-b079-4634f24e320c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Transaction Programs Overview
A processing task accomplished by programs using Advanced Program-to-Program Communications (APPC) is called a transaction. Consequently, programs that use APPC are called transaction programs (TP)s. These programs communicate as peers, on an equal (rather than hierarchical) basis. The TPs use APPC verbs to exchange status information and application data. Each TP uses APPC verbs to supply parameters to APPC, which performs the desired function and returns parameters to the TP.  

 TPs distributed across a local or wide area network perform distributed transaction processing.  

 This section describes how to write TPs and how to configure the systems on which TPs run. The topics in this section cover the following general areas:  

- Understanding fundamental concepts related to TPs  

- Designing and coding TPs  

- Configuring registry and environment variables for invokable TPs  

- Configuring Host Integration Server to work with your TPs  

- Sync Point Level 2 support  

  This section contains:  

- [Communication between TPs](../core/communication-between-tps2.md)  

- [Designing and Coding TPs](../core/designing-and-coding-tps2.md)  

- [Configuring Invokable TPs](../core/configuring-invokable-tps1.md)  

- [Configuring TPs on Host Integration Server](../core/configuring-tps-on-host-integration-server1.md)  

- [Arranging TPs Within an SNA Network](../core/arranging-tps-within-an-sna-network2.md)  

- [Sync Point Level 2 Support in Host Integration Server](../core/sync-point-level-2-support-in-host-integration-server2.md)
