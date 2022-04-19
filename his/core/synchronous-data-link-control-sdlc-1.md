---
description: "Learn more about: Synchronous Data Link Control (SDLC)"
title: "Synchronous Data Link Control (SDLC)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2ee3d53-5456-4ce8-a5f1-a40ab7f67aaa
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Synchronous Data Link Control (SDLC)
SDLC connections use a standard phone line (leased, public, point-to-point, or multidrop). An SDLC adapter within the Host Integration Server computer connects to a modem that uses the phone line to establish a connection with the host system. In a mainframe system, the SDLC connection uses a front end processor (FEP), a communications controller, or an integrated SDLC adapter. In an AS/400 system, the connection goes directly into the AS/400 computer.  
  
 SDLC throughput is limited by the medium used for the connection and the capabilities of the SDLC adapter in the Host Integration Server computer. The cost to implement SDLC grows significantly as faster line types are used. In general, SDLC connections are much slower than 802.2 connections. The following table lists the common line types and their speeds:  
  
|Line type|Typical speed|  
|---------------|-------------------|  
|Analog (conventional phone line)|9600 to 19200 bits per second (BPS)|  
|Digital Data System (DDS)|56 to 64 kilobits per second (Kbps)|  
|Integrated Services Digital Network (ISDN)|56 to 128 Kbps|  
|T1 carrier system|1.544 megabits per second (Mbps)|  
|T3 carrier system|2.048 Mbps|  
  
 SDLC connections are useful for wide-area connections between geographically disparate locations or when bandwidth and usage requirements are low. Because of these factors, SDLC is ideally suited for branch-type deployment strategies.  
  
 Host Integration Server supports SDLC connections using the link support included with Host Integration Server or through an SDLC link service available through various third-party vendors. Not all supported SDLC adapters support all link speeds listed in the previous table.  
  
## See Also  
 [Channel](../core/channel2.md)   
 [Connection Methods](../core/connection-methods2.md)
