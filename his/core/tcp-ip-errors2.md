---
title: "TCP-IP Errors2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9ac196df-1925-45f9-bcec-b42de203f90b
caps.latest.revision: 3
---
# TCP/IP Errors
## TCP/IP 11004  
  
### Causes  
 Your client is configured for Remote client locates servers by name, and you have selected a computer name instead of an IP address. The computer name to IP address resolution has failed, or the IP address resolved cannot be found on the network. Try inputting an IP address instead of a computer name into the client configuration. If this works, then there may be a problem with your local lmhosts file, DNS Server or WINS when using a computer name in the configuration. If this does not work, try pinging the address.  
  
## TCP/IP 10061  
  
### Causes  
 The SNABase service on Host Integration Server computer is not running or the IP address cannot be resolved, either because this Server is not on the network, the IP address is incorrect, or there is a router or network problem. Try pinging the address.  
  
## TCP/IP 121  
  
### Causes  
 The client is configured for Local Client locates servers in a Host Integration Server Subdomain and therefore, is sending out broadcast messages to discover a Host Integration Server computer. These broadcast messages will typically not be passed by a router that may be located in between your client and the server. Go into the client configuration and select Client locates server by name and specify an IP address or computer name of one or more Host Integration Server computers.  
  
## See Also  
 [TCP/IP Clients](../core/tcp-ip-clients1.md)