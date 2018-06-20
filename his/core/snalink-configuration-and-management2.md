---
title: "SNALink Configuration and Management2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12c4fe82-8aa1-498e-850a-0d2ac74f79d4
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SNALink Configuration and Management
The configuration information for a Host Integration Server system is stored in two forms:  
  
- A centralized configuration file containing details of logical units (LUs), physical units (PUs), and connections.  
  
- Entries in the Microsoft Windows registry containing configuration information for the SNALinks supported on that computer. This information contains parameters required by Host Integration Server, and any other parameters that independent hardware vendor (IHV) code may require.  
  
  A Host Integration Server SNALink is defined when a Host Integration Server system is installed. A SNALink can support only one physical connection from the server. If a single adapter is capable of supporting multiple physical connections, Host Integration Server requires multiple SNALinks to be configured.  
  
  To reconfigure a server's SNALink support (for example, after installing a new adapter), the administrator uses either the Windows Network Control Panel applet or the Host Integration Server setup program. For further information about how this operates, see [Setup Information](../core/setup-information-snadis-1.md).  
  
  All other configuration of a Host Integration Server system is performed using SNA Manager. As part of the configuration process, logical connections to remote PUs are associated with one or more SNALinks.  
  
  All configured SNALinks are automatically started when the Host Integration Server system is started. At this stage, the SNALink performs any initialization required, and then waits for instructions from local nodes.  
  
  When a connection is activated, either from SNA Manager or automatically (for example, in response to a 3270 user's request for a session with a remote host), the SNALink receives an Open(LINK) message from the local node. The SNALink should then perform whatever action is required to initiate that connection. This can involve dialing a telephone number for a switched Synchronous Data Link Control (SDLC) connection or bringing up level 2 on an X.25 link and sending a CALL packet.  
  
  If the IHV wants the same physical adapter to be available for use by multiple SNALinks (for example, a dumb SDLC card can be used to communicate using SDLC or X.25 protocols), the SNALink should not attempt to access the hardware until it has received an **Open(LINK)** message from the local node.