---
description: "Learn more about: Opening the SSCP Connection"
title: "Opening the SSCP Connection1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7ff5c44-3fbd-413f-93be-49308f2a1fcc
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Opening the SSCP Connection
An application gains access to the system services control point (SSCP) session by opening an SSCP connection to the local node. To do this, an application sends an [Open(SSCP) Request](./open-sscp-request2.md) message to the local node, which responds with an [Open(SSCP) Response](./open-sscp-response1.md). The local node follows a positive **Open(SSCP) Response** with a [Status-Session](./status-session2.md) message reporting the current state of the SSCP session. (For more information, see [Using the SSCP Session](../core/sscp-session2.md).)  
  
 The following figure shows the message flow. For a figure showing a more detailed message flow, including locality, partner, index (LPI) values used during initialization of both the SSCP and primary logical unit (PLU) sessions, see [Opening the PLU Connection](../core/opening-the-plu-connection1.md).  
  
 ![](../core/media/his-32703c.gif "his_32703c")  
Message flow between a local node and an application  
  
## In This Section  
  
-   [LU Groups](../core/lu-groups1.md)  
  
-   [Resource Location for Open SSCP](../core/resource-location-for-open-sscp2.md)
