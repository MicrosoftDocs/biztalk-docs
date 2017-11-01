---
title: "Screening Routers and Internet Firewalls1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b764d512-5a28-484b-baf5-429801d63bd2
caps.latest.revision: 4
---
# Screening Routers and Internet Firewalls
You can configure destination port numbers in Host Integration Server for End-user and Administrator clients using TCP/IP.  
  
 Each network transport has the following three components for which you can assign destination ports.  
  
## DatagramPort  
 This port is used for datagram (mostly broadcast or multicast) traffic. Use the **Server Broadcasts** dialog box in Host Integration Server SNA Manager to control which transport is used for Server-to-Server communication.  
  
## SnaBasePort  
 This is the port to which the server SnaBase listens for new client sponsor connections. Sponsor connections are used by the Host Integration Server client to learn about the SNA subdomain in which it participates.  
  
## SnaServerPort  
 This is the port where the SNASERVR.EXE waits for new application session requests.  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security.md)