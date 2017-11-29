---
title: "Choosing Network Protocols for Host Integration Server1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76ac1a1d-a20d-4215-b8a1-d34a6cc0f808
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Choosing Network Protocols for Host Integration Server
After you determine the server-to-host connection, you must choose the protocols to use for two additional [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] communication paths: client/server communication and server/server communication. You can use one protocol for both, or you can use a combination of different protocols, if all servers share at least one client/server protocol and use it for server/server communication.  
  
 Deploying a single protocol across your wide area network (WAN) is the easiest way to manage your communications. The following figure shows a network in which TCP/IP is used for all types of communication involving Host Integration Server computers and clients.  
  
 ![](../core/media/dep08.gif "dep08")  
Diagram of network using TCP/IP for both server-to-server and server-to-client communication  
  
 You may decide to gradually implement Host Integration Server throughout your enterprise, in which case you may need to use existing protocols for certain connections.  
  
 ![](../core/media/dep09.gif "dep09")  
Diagram of network using NetBEUI for server-to-server communication and for server-to-client communication  
  
## In This Section  
 [Choosing Client/Server Network Protocols](../core/choosing-client-server-network-protocols.md)  
  
 [Choosing Server/Server Network Protocols](../core/choosing-server-server-network-protocols.md)  
  
## See Also  
 [Connecting Servers](../core/connecting-servers.md)