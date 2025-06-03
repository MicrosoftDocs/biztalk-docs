---
description: "Learn more about: Screening Routers and Internet Firewalls"
title: "Screening Routers and Internet Firewalls1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
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
 [Understanding Windows Security](../core/understanding-windows-security1.md)
