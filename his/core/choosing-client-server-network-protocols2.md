---
title: "Choosing Client-Server Network Protocols2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82077160-f96b-4157-9714-5291b35bebe1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Choosing Client/Server Network Protocols
Host Integration Server client computers can communicate through a number of different local area APIs or network transports: Microsoft Networking (Named Pipes), or TCP/IP (sockets). The network software and the Host Integration Server software must be installed correctly on both clients and servers for them to handle different protocols correctly. Correct installation ensures two essential aspects of communication:  
  
- Host Integration Server computers and client computers are visible to each other on the LAN. This results when the network software is installed correctly on all affected computers.  
  
- Host Integration Server computers communicate with clients over the correct LAN protocol. Clients direct their communication to the correct subdomain name or (for some clients using Microsoft Networking (Named Pipes) or TCP/IP) to one or more correct server names.  
  
  TCP/IP is the standard network protocol for client/server applications. Its high performance and routing ability make it suitable for many wide area network (WAN) environments. In many cases, TCP/IP will be the best protocol choice for your network, especially if TCP/IP is already deployed to some degree in the LAN segment on which the Host Integration Server computers and clients reside.  
  
## See Also  
 [Choosing Network Protocols for Host Integration Server](../core/choosing-network-protocols-for-host-integration-server1.md)   
 [Choosing Server/Server Network Protocols](../core/choosing-server-server-network-protocols2.md)   
 [Installing Host Integration Server Clients](../core/installing-host-integration-server-clients2.md)