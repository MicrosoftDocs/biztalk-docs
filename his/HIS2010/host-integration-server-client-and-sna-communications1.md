---
title: "Host Integration Server Client and SNA Communications1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf4480c4-287e-4db0-92ef-e4c0c59277c8
caps.latest.revision: 4
---
# Host Integration Server Client and SNA Communications
When a client computer makes an SNA request, the client computer must direct that request to a domain or to one or more [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computers. The appropriate way for a client computer to direct requests depends on the protocol used and the relative location of client computers and servers. The following table lists the ways that client computers direct SNA requests, and the information that will be requested by Setup during client software installation.  
  
|Network protocol used on client|How the client directs SNA requests|Information to find out before running client setup|  
|-------------------------------------|-----------------------------------------|---------------------------------------------------------|  
|Microsoft Networking|Either to the local domain (if the Host Integration Server computers are in the same domain as the client computer), or to one or two specific Host Integration Server computers in a remote domain.|Whether the client computer is in the same domain as the Host Integration Server computers, and if not, one or two names of Host Integration Server computers.|  
|TCP/IP|Either to a domain name or to a specific server name, depending on what is specified in the SNA Client Mode or Host Integration Server Location dialog box.|Contact your network administrator for additional information regarding a specific IP address for Host Integration Server.|  
  
 When a client computer first makes a request for communication with the SNA network, it establishes an initial connection (the sponsor connection) with a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer. The client computer then requests a logical unit (LU), either by name or by requesting an LU from a particular pool of LUs. If the request is for a particular LU, the sponsor server responds by providing the name of the Host Integration Server computer that contains the LU. If the request is for an LU pool, the sponsor server responds by providing the client computer with all the names of Host Integration Server computers in its subdomain that support the pool. From these names, the client computer picks a server at random.  
  
 Host Integration Server computers and client computers keep track of the names of servers in the SNA subdomain through the SnaBase service (formerly known as the network access protocol, or NAP). For client computers, the sponsor connections, along with the SnaBase provide a view into the server subdomain.  
  
## See Also  
 [SNA Service](../HIS2010/sna-service1.md)