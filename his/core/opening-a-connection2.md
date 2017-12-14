---
title: "Opening a Connection2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8d0c453-d0b9-44fb-8d79-15dfcdc1856a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Opening a Connection
Before a locality partner index (LPI) connection can be used to transfer data, it needs to be opened. This is performed by sending Open messages, starting with an Open request. The format of an Open message is defined by the interface being used. For example, the 3270 emulator uses the function management interface (FMI) to communicate with the local 2.1 node.  
  
 The interface also defines the initiator of the Open request. In this case, the 3270 emulator sends the [Open(SSCP) Request](./open-sscp-request2.md), and the local 2.1 node sends the [Open(PLU) Request](./open-plu-request2.md).  
  
 On the **Open(SSCP) Request**, the 3270 emulator sets all the source and destination LPIs to zero, except for the source index, which can be used by the 3270 emulator for internal routing (for example, to distinguish between two sessions).  
  
 The DL-BASE and Dynamic Access Module (DMOD) ensure that Open messages are routed to a suitable destination. If a routing procedure is used, it should always first call [sbpurcvx](./sbpurcvx1.md) to process Open responses. When **sbpurcvx** indicates that it has not processed a received message, and the received message is an Open OK response, the application is informed that the connection was established successfully.