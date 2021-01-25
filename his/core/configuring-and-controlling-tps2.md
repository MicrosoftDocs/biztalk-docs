---
description: "Learn more about: Configuring and Controlling TPs"
title: "Configuring and Controlling TPs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a081d6a-2c75-4e22-9597-69702e7b5c0d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Configuring and Controlling TPs
The following table shows how the characteristics of the transaction programs (TPs) and selection of the logical units (LUs) for a conversation are controlled.  
  
|Characteristic|How controlled|  
|--------------------|--------------------|  
|Type of verb: synchronous or asynchronous|Written into the code. Synchronous verbs use blocking calls; asynchronous verbs avoid blocking calls. See [Receiving Data Asynchronously](../core/receiving-data-asynchronously1.md) and [WinAsyncAPPC](./winasyncappc1.md).|  
|Type of conversation:  basic or mapped|Written into the code. The **MC_** prefix is used on verbs in mapped conversations and omitted on verbs in basic conversations. For two TPs to communicate successfully, both must use the same type of conversation, basic or mapped. See [Basic and Mapped Conversations Compared](../core/basic-and-mapped-conversations-compared2.md).|  
|Type of TP:  invoking or invokable|Written into the code. Invoking TPs start with [TP_STARTED](./tp-started2.md), which identifies the invoking TP, and [ALLOCATE](./allocate2.md) or [MC_ALLOCATE](./mc-allocate2.md), which identifies the requested invokable TP. Invokable TPs start with [RECEIVE_ALLOCATE](./receive-allocate1.md), which identifies the invokable TP. See [Invoking TPs](../core/invoking-tps2.md) and [Invokable TPs](../core/invokable-tps2.md).|  
|The local LU alias to be used by an invoking TP|Three options:<br /><br /> -   Written into the code in [TP_STARTED](./tp-started2.md).<br />-   Configured (in Host Integration Server Manager as the default local APPC LU for the user who starts the invoking TP.<br />-   Configured as a member of the default outgoing local APPC LU pool using the SNA Manager on Host Integration Server.<br /><br /> See [Configuring Invoking TPs on Host Integration Server](../core/configuring-invoking-tps-on-host-integration-server2.md).|  
|The invokable TP requested by an invoking TP|Written into the [ALLOCATE](./allocate2.md) or [MC_ALLOCATE](./mc-allocate2.md) request in the invoking TP.|  
|The LU alias to be used by an invokable TP|Two options:<br /><br /> -   Written into the invoking TP (not the invokable TP), in [ALLOCATE](./allocate2.md) or [MC_ALLOCATE](./mc-allocate2.md).<br />-   Configured as the default remote APPC LU for the user who starts the invoking TP.<br /><br /> See [Configuring Invoking TPs on Host Integration Server](../core/configuring-invoking-tps-on-host-integration-server2.md) and [Matching Invoking and Invokable TPs](../core/matching-invoking-and-invokable-tps1.md).|  
|Type of autostarted invokable TP: queued or nonqueued|Configured with registry or environment variables. See [Configuring Invokable TPs](../core/configuring-invokable-tps1.md).|  
|Local LU and remote LU aliases|Configured using SNA Manager on Host Integration Server.|  
|The pairing of local and remote LUs, and the mode used for each LU-LU pair|Configured using SNA Manager on Host Integration Server.|
