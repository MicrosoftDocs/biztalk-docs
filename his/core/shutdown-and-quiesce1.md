---
description: "Learn more about: Shutdown and Quiesce"
title: "Shutdown and Quiesce1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5c5e629-1230-4a00-b38d-b76ba2f58fb4
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Shutdown and Quiesce
Both shutdown and quiesce protocols involve a half-session entering a quiesced state, in which it cannot send any more normal flow requests, but must continue to receive and respond to requests from its session partner. The essential differences are that shutdown can only be initiated by the host and only requires that the secondary quiesce as soon as is convenient (usually at the end of a bracket). Quiesce can be initiated by both the host and the application and requires that the recipient quiesce at the end of the chain.  
  
 If the application has been quiesced but still attempts to send inbound [Data](./data1.md) messages, they will be rejected with [Status-Acknowledge(Nack-2)](./status-acknowledge-nack-2-2.md) messages. The application can, however, continue to generate status messages.  
  
## In This Section  
  
-   [Shutdown](../core/shutdown2.md)  
  
-   [Quiesce](../core/quiesce1.md)
