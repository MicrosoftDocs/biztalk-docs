---
title: "Communication Between Host Integration Server Computers and a Host Computer1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 85079a04-6f71-4b5e-9667-ee226ab2f805
caps.latest.revision: 4
---
# Communication Between Host Integration Server Computers and a Host Computer
Within the context of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], a connection is the data communication path between a Host Integration Server computer and an IBM host (mainframe or AS/400). A connection corresponds to a physical unit (PU) definition on a mainframe or an APPC controller definition on an AS/400. The connection is what makes it possible for a personal computer on the LAN to communicate with a host by means of a Host Integration Server computer. Note that SNA connections do not use BISYNC, an older IBM standard for communications.  
  
 The following figure shows a Host Integration Server network connected to an IBM mainframe.  
  
 ![](../core/media/snas01.gif "snas01")  
Host Integration Server network connected to IBM mainframe  
  
 For each physical adapter or connection, an appropriate link service is installed and configured within Host Integration Server. The link service is a Windows server service or device driver that is used to control server-to-host communication adapters supported by Host Integration Server. The link service provides the SNA data link-level protocol used by the Host Integration Server computer to communicate with the host.  
  
 After being configured, the link service is available for use not only on the configured Host Integration Server, but also on any Host Integration Server computer in the subdomain using the Distributed Link Service feature of Host Integration Server.  
  
 After a link service is configured, you can create connections. A link service may support multiple links to one or more hosts.  
  
 In SNA terms, the combination of a connection and the link service it uses is equivalent to a PU. In hierarchical SNA networks, Host Integration Server provides PU 2.0 functionality. For peer-oriented SNA networks, Host Integration Server provides PU 2.1 LEN node functionality.  
  
 In this Section  
  
 [Physical Unit (PU)](../HIS2010/physical-unit-pu-2.md)  
  
 [Logical Unit (LU)](../HIS2010/logical-unit-lu-2.md)  
  
 [Choosing a Connection Type](../HIS2010/choosing-a-connection-type2.md)  
  
## See Also  
 [SNA Service](../HIS2010/sna-service1.md)