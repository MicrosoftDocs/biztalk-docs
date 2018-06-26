---
title: "Overview of Network Protocols for Clients2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4f96b1f5-13ec-4ece-bd0d-e084c91090e3
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Overview of Network Protocols for Clients
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] clients can communicate with servers through the following LAN protocols:  
  
-   Microsoft Networking (Named Pipes)  
  
-   TCP/IP  
  
> [!IMPORTANT]
>  In order for the different client/server protocols to be handled correctly by Host Integration Server, both clients and servers must have the network software and the Host Integration Server software installed correctly. Be sure to follow the installation instructions in this section carefully, and follow the installation instructions for other software you are using for example, Windows Server and the associated network software, Host Integration Server, and network software on clients.  
  
 Correct installation of network and Host Integration Server on servers and clients ensures that two essential aspects of communication work correctly:  
  
- The servers and clients are visible to each other on the local area network (LAN). This results when the network software is installed correctly on all affected computers.  
  
- The Host Integration Server computers communicate with clients over the correct LAN protocol, and the clients direct their communication to the correct domain name or, for some clients using Microsoft Networking or TCP/IP, to one or more correct server names. A Host Integration Server client must be set up to use the correct server or domain name or, for Microsoft Networking, set up to locate servers in the local domain. Otherwise, the client will not be able to locate a Host Integration Server computer.  
  
  For information about how Host Integration Server enables you to view and choose the domain and protocols to be used by Host Integration Server computers and clients, see [Important Network Options on a Host Integration Server Computer](../core/important-network-options-on-a-host-integration-server-computer2.md). For details about how each of the network protocols works on a Host Integration Server client, see the section about that specific network protocol (for example, [TCP/IP Clients](../core/tcp-ip-clients2.md)).  
  
## In This Section  
 [Client Logons and the Storing of Passwords](../core/client-logons-and-the-storing-of-passwords1.md)  
  
 [Types of Client Logons](../core/types-of-client-logons1.md)  
  
## See Also  
 [Planning Client/Server Communication](../core/planning-client-server-communication2.md)