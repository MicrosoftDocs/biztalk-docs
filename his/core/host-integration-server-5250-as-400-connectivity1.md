---
title: "Host Integration Server 5250 (i Series) Connectivity"
description: "Learn more about Host Integration Server 5250 (i Series) connectivity."
ms.prod: host-integration-server
ms.topic: conceptual
ms.date: 11/30/2017
---

# Host Integration Server 5250 (i Series) Connectivity

In the peer-oriented SNA network model, all computers on the network can communicate directly with each other. Advanced Peer-to-Peer Networking (APPN) enables distributed data processing, defines how components communicate with each other, and determines the level of network-related services that are supplied by each computer in the network. Although peer-oriented SNA networks are usually associated with an i Series host system, mainframe systems can also support peer-to-peer networking.  
  
IBM i Series computers use the 52xx series of devices. In particular, 5250 describes the terminal display data stream. The Advanced Program-to-Program Communications (APPC) protocol is used to support 5250 terminals and other APPN network computers, devices, and programs to communicate with each other. Each device in an APPN network is known as a type 2.1 physical unit (PU 2.1). In addition, the APPC protocol defines associated logical units as APPC LUs (also called LU 6.2).  

![Image that shows communications in a peer-oriented network.](../core/media/srvc05.gif)  

## Communications in a peer-oriented network  
  
In an APPN network, Host Integration Server computers emulate PU 2.1 devices and can connect to an i Series using IP-DLC.

## See also

- [APPC](../core/appc1.md)
- [IBM System i 5250 Terminal Connections](../core/as-400-5250-terminal-connections1.md)
- [Understanding Connectivity](../core/understanding-connectivity1.md)
