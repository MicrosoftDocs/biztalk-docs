---
title: "XID Retries2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69896b9f-c413-4879-9dfa-46eafd08fb44
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# XID Retries
When the local node specifies that the SNALink is to send an exchange identification (XID), either by supplying it on the [Open(LINK) Request](./open-link-request1.md) or by sending it on a [Send-XID](./send-xid1.md) message, it is the responsibility of the SNALink to perform any retries.  

 XIDs need to be retried because:  

- The remote station has not been started yet.  

- Frames may be lost on the line due to noise.  

  Synchronous Data Link Control (SDLC) SNALinks should implement a contact time-out and a retry limit—values for these are provided on the [Open(LINK)](./open-link-1.md) message. The time-out specifies how often the XID should be retried, and the retry limit specifies how many XIDs should be sent before abandoning the connection activation and sending an [Outage](./outage2.md) message to the local node. The SNALink should stop retrying the XID when one of the following occurs:  

- It receives an XID from the remote station.  

- An [Open(STATION)](./open-station-1.md) message is received from the node.  

- A mode-setting command is received on the link.
