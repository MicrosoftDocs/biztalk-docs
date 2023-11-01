---
title: Choosing Server-to-Host Connections
description: Learn more about choosing server-to-host connections.
ms.prod: host-integration-server
ms.topic: conceptual
ms.date: 11/30/2017
---

# Choosing Server-to-Host Connections

In [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] terms, a host connection is the data communications path between Host Integration Server and a host system. For a mainframe, the connection corresponds to a physical unit (PU) definition in Virtual Telecommunications Access Method (VTAM). On the i Series computer, the connection corresponds to an Advanced Program-to-Program Communications (APPC) controller definition.
  
For each adapter or connection, you configure an link service within Host Integration Server. A link service is a Windows-based service or device driver that is used to control server-to-host communication adapters supported by Host Integration Server. Today, IP-DLC is the only supported link service. After you configure the IP-DLC link service, you can configure the connections. Using a host connection, a client computer can communicate with the mainframe system.
  
In SNA terms, a physical unit (PU) is the combination of a physical connection and the link service it uses. In an SNA network, Host Integration Server provides PU 2 or PU 2.1 functionality.
     
## In This Section

[Mainframe Connection Summary](../core/mainframe-connection-summary1.md)  
  
[AS/400 Connection Summary](../core/as-400-connection-summary1.md)  
  
## See also

[Connecting Servers](../core/connecting-servers2.md)
