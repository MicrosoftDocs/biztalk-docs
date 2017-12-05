---
title: "Communication Between Host Integration Server Computers and Client Computers2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10e129da-34a1-437d-81d0-c424347dd716
caps.latest.revision: 5
---
# Communication Between Host Integration Server Computers and Client Computers
Client computers locate the resources of the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer in either one of two ways:  
  
-   Sponsor connection  
  
-   Active Directory directory service  
  
 A sponsor connection is created when a client computer makes a request to communicate with a Host Integration Server computer and an initial connection is established. The first Host Integration Server computer to respond to the request (called the sponsor computer) provides the client computer with all the names of Host Integration Server computers in the subdomain. From these names, the client computer locates an available LU or LU pool.  
  
 In a similar way, a client computer that is configured to use Active Directory makes a request to the Active Directory database. Active Directory responds to the request and provides the client computer with all the names of Host Integration Server computers in the Organizational Unit.  
  
 For client/server protocols to operate properly with Host Integration Server, both client computers and servers must have the network software and the Host Integration Server software installed properly. The network protocols available for use by various client operating systems include Microsoft Networking (Named Pipes) and TCP/IP.  
  
 In this Section  
  
 [Host Integration Server Client and SNA Communications](../core/host-integration-server-client-and-sna-communications1.md)  
  
## See Also  
 [SNA Service](../core/sna-service1.md)