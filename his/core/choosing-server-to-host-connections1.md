---
title: "Choosing Server-to-Host Connections1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f93fd89f-4ef4-47d4-8345-51cb31ba3179
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Choosing Server-to-Host Connections
In [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] terms, a host connection is the data communications path between Host Integration Server and a host system. For a mainframe, the connection corresponds to a physical unit (PU) definition in Virtual Telecommunications Access Method (VTAM). On the AS/400 computer, the connection corresponds to an Advanced Program-to-Program Communications (APPC) controller definition.  
  
 For each physical adapter or connection, you install and configure an appropriate link service within Host Integration Server. A link service is a Windows-based service or device driver that is used to control server-to-host communication adapters supported by Host Integration Server. Once configured, the link service is available for use not only on the configured Host Integration Server computer, but also on any server in the subdomain using the Distributed Link Service (DLC) feature. See [Distributed Link Service](./distributed-link-service1.md) for more information.  
  
 After you configure the link services, you can configure the connections. Using a host connection, a client computer on a LAN can communicate with the mainframe system. For some link services, it is possible to define multiple connections over a single host link.  
  
 In SNA terms, a physical unit (PU) is the combination of a physical connection and the link service it uses. In an SNA network, Host Integration Server provides PU 2 or PU 2.1 functionality similar to that of an IBM cluster controller.  
  
 Several factors should be taken into account when determining a physical connection method to your mainframe:  
  
- Performance requirements  
  
- Expected server loads  
  
- Existing network infrastructure  
  
- Chosen Host Integration Server deployment model  
  
- Cost  
  
  You should plan for enough future capacity to support additional connections to your host system. Ethernet connections are the best choice for an all-purpose connection to a host.  
  
  For some link services, multiple host connections are possible using a single adapter, most notably the IP-DLC link service. Host Integration Server supports up to 250 host connections per server. Up to four instances of Host Integration Server are supported on a single computer.  
  
## In This Section  
 [Mainframe Connection Summary](../core/mainframe-connection-summary1.md)  
  
 [AS/400 Connection Summary](../core/as-400-connection-summary1.md)  
  
## See Also  
 [Connecting Servers](../core/connecting-servers2.md)