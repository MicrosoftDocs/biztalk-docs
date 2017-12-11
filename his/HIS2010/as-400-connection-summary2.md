---
title: "AS-400 Connection Summary2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 295b9e21-7e00-4964-986f-b14d7e2799e4
caps.latest.revision: 3
---
# AS/400 Connection Summary
In the peer-oriented SNA network model, all computers on the network can communicate directly with each other. Advanced Peer-to-Peer Networking (APPN) is the architecture developed by IBM that enables distributed data processing. APPN defines how components communicate with each other, and the level of network-related services, like routing sessions, that are supplied by each computer in the network.  
  
 ![](../core/media/dep07.gif "dep07")  
Diagram showing Host Integration Server connecting to an AS/400 with several connection methods  
  
 In an APPN network, Host Integration Server emulates a type 2.1 physical unit device (PU 2.1). Host Integration Server computers can connect to an AS/400 computer using several connection methods:  
  
-   Token Ring  
  
-   Ethernet  
  
-   FDDI  
  
-   SDLC  
  
 Frame relay or bridging solutions can also be implemented to transport SNA traffic over wide area network (WAN) connections in branch-based deployment models. Host Integration Server operates as an APPN low-entry networking (LEN) node and communicates with other APPN nodes using the Advanced Program-to-Program Communications (APPC) or LU 6.2 protocol.  
  
## See Also  
 [Choosing Server-to-Host Connections](../HIS2010/choosing-server-to-host-connections2.md)   
 [Mainframe Connection Summary](../HIS2010/mainframe-connection-summary2.md)