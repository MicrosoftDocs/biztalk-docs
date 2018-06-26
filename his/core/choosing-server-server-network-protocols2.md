---
title: "Choosing Server-Server Network Protocols2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04f2a706-62b9-49f9-9856-416d5ddb728e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Choosing Server/Server Network Protocols
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computers communicate with each other using mailslot messages or directed datagrams over a network. Host Integration Server enables you to make choices concerning these broadcasts.  
  
 You can select among the following protocols for server broadcasts: Microsoft Networking (Named Pipes), and TCP/IP.  
  
> [!IMPORTANT]
>  You must make sure that at least one protocol is available on all [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computers in the subdomain, and that this protocol is used for server/server communication and client/server communication.  
> 
> [!NOTE]
>  For example, if all [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computers in a subdomain use TCP/IP, the protocol used for server/server communication must be TCP/IP, and all servers must use TCP/IP for client/server communication as well.  
  
 Using multiple server/server transport protocols can add significantly to network overhead. This is because every server broadcast must be sent out through all protocols selected in the Host Integration Server management console.  
  
 For highest efficiency, select only one protocol for broadcasts between Host Integration Server computers. Remember that the protocol must be available on all Host Integration Server computers in the subdomain. Where multiple choices are available (multiple protocols are bound to the network adapters on all Host Integration Server computers), select a protocol other than Microsoft Networking (Named Pipes). This is recommended because of design requirements for mailslot broadcasts. When these broadcasts are sent over Microsoft Networking (Named Pipes), there is the local system cannot determine which protocol the receiving system will be using, so the broadcast is sent over all protocols bound to the local adapter. This causes multiple mailslot broadcasts by means of Microsoft Networking (Named Pipes) for adapters to which several protocols are bound. The multiple broadcasts cause an increase in network traffic.  
  
 In subdomains in which all Host Integration Server adapters can use multiple protocols, TCP/IP protocol is recommended. You may be able to select extra protocols that do not exist in your network. However, selecting these has no effect.  
  
 The Host Integration Server management console also allows you to specify a parameter called Mean Time Between Server Broadcasts. For optimum efficiency, you should specify a value greater than or equal to 60 seconds (the default). The smaller this value, the less the efficiency, but the more likely the broadcasts will compensate for lost messages. It is recommended that you choose a value of 120 seconds or greater initially. If you encounter an increased number of lost messages, this value should be reduced until a low number of messages are lost.  
  
## See Also  
 [Choosing Network Protocols for Host Integration Server](../core/choosing-network-protocols-for-host-integration-server1.md)   
 [Choosing Client/Server Network Protocols](../core/choosing-client-server-network-protocols2.md)   
 [Installing Host Integration Server Clients](../core/installing-host-integration-server-clients2.md)