---
title: "Multiple Connections2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d086346-0f0c-4bac-8417-9bc2d72d67ca
caps.latest.revision: 3
---
# Multiple Connections
For 802.2 and X.25 links, multiple connections can use the same physical link supported by a single instance of the SNALink software.  
  
 For each connection to a remote station, there is a LINK LPI connection and a STATION LPI connection (this is different from Synchronous Data Link Control (SDLC) multipoint as described in [SDLC Multipoint Connections](../HIS2010/sdlc-multipoint-connections2.md)). Hence, there can be multiple pairs of LPI connections between a local node and an SNALink. For each connection, the local node issues an [Open(LINK) Request](../HIS2010/open-link-request2.md) and, after exchange identification (XID) exchange, an [Open(STATION) Request](../HIS2010/open-station-request1.md).  
  
 The local node is configured with a maximum number of connections that can be active at any one time. In addition, each potential connection is configured with the address of the remote station. This information is required when activating a connection, and is included in the **Open(LINK) Request** for an outgoing connection.