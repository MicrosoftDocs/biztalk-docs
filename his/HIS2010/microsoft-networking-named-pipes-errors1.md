---
title: "Microsoft Networking (Named Pipes) Errors1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad7a85da-d082-46e2-b594-f2204d2c1652
caps.latest.revision: 3
---
# Microsoft Networking (Named Pipes) Errors
## NAMED PIPES 5  
  
### Causes  
 One of the following has occurred:  
  
-   Access has been denied trying to create a connection to the Host Integration Server computer. The client/server interface connects to the Host Integration Server computer just like any other local area network (LAN) connection. It must be validated by Windows as a valid user in the domain.  
  
-   The Host Integration Server computer is unreachable. If using TCP/IP this could mean that the name to IP address resolution has failed.  
  
## NAMED PIPES 2  
  
### Causes  
 The client has connected to the Host Integration Server computer, but the SNABase service is not running on that machine. Start the SNABase service on the Host Integration Server computer to which you are trying to connect.  
  
## NAMED PIPES 121  
  
### Causes  
 The client is configured for **Client locates servers in an Host Integration Server 2009 Subdomain** and therefore, is sending out broadcast messages to discover a Host Integration Server computer. These broadcast messages will typically not be passed by a router that may be between your client and the server. In the client configuration select **Client locates server by name** and specify an IP address or computer name of one or more Host Integration Server computers.  
  
## See Also  
 [Named Pipes Clients](../HIS2010/named-pipes-clients1.md)