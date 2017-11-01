---
title: "Multiple Connections1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48cf0edc-1416-4810-a09a-ca0af7bd1a9c
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Multiple Connections
For 802.2 and X.25 links, multiple connections can use the same physical link supported by a single instance of the SNALink software.  
  
 For each connection to a remote station, there is a LINK LPI connection and a STATION LPI connection (this is different from Synchronous Data Link Control (SDLC) multipoint as described in [SDLC Multipoint Connections](../core/sdlc-multipoint-connections.md)). Hence, there can be multiple pairs of LPI connections between a local node and an SNALink. For each connection, the local node issues an [Open(LINK) Request](../Topic/Open\(LINK\)%20Request2.md) and, after exchange identification (XID) exchange, an [Open(STATION) Request](../Topic/Open\(STATION\)%20Request1.md).  
  
 The local node is configured with a maximum number of connections that can be active at any one time. In addition, each potential connection is configured with the address of the remote station. This information is required when activating a connection, and is included in the **Open(LINK) Request** for an outgoing connection.