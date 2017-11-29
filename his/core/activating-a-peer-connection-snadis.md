---
title: "Activating a Peer Connection (SNADIS)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3374a4b-829e-4e61-966c-c150893970e5
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Activating a Peer Connection (SNADIS)
For a peer connection, there is an activation sequence that involves the two stations exchanging format 3 exchange identification (XID) frames. As part of this sequence, the two stations agree on their link roles. They also exchange information relating to the link level connection, such as the maximum frame size supported.  
  
 The node passes XIDs to the SNALink over the LINK LPI connection using the [Send-XID](../Topic/Send-XID2.md) message. The SNALink returns received XIDs to the local node over the LINK LPI connection using the [Request-Open-Station](../Topic/Request-Open-Station1.md) message.  
  
 [Fixed Link Roles](../core/fixed-link-roles.md) and [Negotiable Link Roles](../core/negotiable-link-roles.md) show examples of XID exchange for the two cases:  
  
-   The link roles are explicitly configured for the two stations.  
  
-   The link roles of both stations are negotiable.  
  
 Points to note are:  
  
-   The [Open(LINK) Request](../Topic/Open\(LINK\)%20Request2.md) is supplied with a NULL XID that is sent when the end-to-end connection is established.  
  
-   After the first NULL XID, all XIDs are format 3.  
  
-   If both stations are set up to be negotiable, the station with the higher node identifier becomes the primary.  
  
-   If both stations are negotiable and have the same node identifier, both stations produce randomized node identifiers that are compared as before.  
  
## In This Section  
  
-   [Fixed Link Roles](../core/fixed-link-roles.md)  
  
-   [Negotiable Link Roles](../core/negotiable-link-roles.md)