---
description: "Learn more about: Host Integration Server Client and SNA Communications"
title: "Host Integration Server Client and SNA Communications2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12e64359-c62f-4492-98b2-9766dfa44c74
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Host Integration Server Client and SNA Communications
When an application on a client computer makes a call to one of our SNA APIs, the client computer must direct a resource location request to the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer that is its sponsor server. 
  
 When a client computer first makes a request for communication with the SNA network, it establishes an initial connection (the sponsor connection) with a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer. The client computer then requests a logical unit (LU), either by name or by requesting a particular pool of LUs. If the request is for a specific LU, the sponsor server responds by providing the name of the Host Integration Server computer that contains the LU. If the request is for an LU pool, the sponsor server responds by providing the client computer with all the names of Host Integration Server computers in its subdomain that support the pool. From these names, the client computer picks a server at random.  
  
 Host Integration Server computers and client computers keep track of the names of servers in the SNA subdomain through the SnaBase service. For client computers, the sponsor connections, along with the SnaBase provide a view into the server subdomain.  
  
## See Also  
 [SNA Service](../core/sna-service2.md)
