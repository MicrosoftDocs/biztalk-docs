---
description: "Learn more about: Important Network Options on a Client"
title: "Important Network Options on a Client1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Important Network Options on a Client
For [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] client software, several key options supply the information a client must have for locating Host Integration Server computers. These options specify which protocol the client uses to communicate with Host Integration Server computers if more than one protocol is available on the client, and which domain or server names the client will direct SNA requests to.  
  
 When a client makes an SNA request, the client must direct that request to a domain or to one or more Host Integration Server computers. The appropriate way for a client to direct requests depends on the protocol used and the relative location of clients and servers. The following table lists the ways clients direct SNA requests, and the information that will be requested by setup during client installation. For more detail about how a client directs requests and locates Host Integration Server computers, see the section about the appropriate type of client (for example, [Clients Using TCP/IP](../core/tcp-ip-clients2.md)).  
  
|Network protocol used on client|How the client directs SNA requests|Information to find out before running client setup|  
|-------------------------------------|-----------------------------------------|---------------------------------------------------------|  
|Microsoft Networking|Either to the local domain (if the Host Integration Server computers are in the same domain as the client), or to one or two specific Host Integration Server computers in a remote domain.|Whether the client is in the same domain as the Host Integration Server computers, and if not, one or two names of Host Integration Server computers.|  
|TCP/IP|Either to a domain name or to specific server name, depending on what is specified in the Host Integration Client Mode or Host Integration Server Location dialog box.|Contact your network administrator for additional information regarding a specific IP address for the Host Integration Server computer.|  
  
## See Also  
 [Important Host Integration Server Network Options](../core/important-host-integration-server-network-options1.md)
