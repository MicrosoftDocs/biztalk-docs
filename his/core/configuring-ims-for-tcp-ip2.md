---
title: "Configuring IMS for TCP-IP2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5773466d-144b-4c4e-be5d-5443773b5a6d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring IMS for TCP/IP
This section describes the necessary steps in configuring IMS for TCP/IP. It may also be necessary to set up and configure the Host Web Service. See your IBM documentation for information on this.  
  
## IMS TCP/IP Platform Requirements  
  
-   TCP/IP version 3R2  
  
-   IMS version 4 or later  
  
## Connections to IMS using TCP/IP  
 IMS uses a Listener (program EZAIMSLN) to establish an interaction with TCP/IP. The Listener in an IMS Batch Message Processing (BMP) helps facilitate the connection process. When the Listener starts, it obtains a socket on which it can "listen" for connection requests from TCP/IP. The Listener binds the socket to a specified port, and then waits for a client request on that port.  
  
 TCP/IP maintains a relationship of a port number to an IMS Listener BMP. When a client makes a request on a port associated with IMS, TCP/IP forwards the connection request to the Listener in that BMP.  
  
## TCP/IP-to-IMS Configuration  
 A TCP/IP port number is associated with an IMS Batch Processing Region (BPR) in the TCP/IP profile data set (hlq.PROFILE.TCPIP). The port statement is used to define this relationship. For example, the following is a port statement associating port 3000 with an IMS batch region with a job name of WNWIBR1:  
  
```  
3000 TCP WNWIBPR1  
  
```  
  
## IMS-to-TCP/IP Configuration  
 You can start an IMS Message Processing Program by specifying the program name of the IBM-supplied Listener program (EZAIMSLN). The Listener reads a configuration file identified by the DD statement **LSTNCFG**. This configuration data set contains one or more of the following startup parameter statements (one set for each transaction defined for at least one Command Region):  
  
- `TCPIP` statement.  Identifies the job name for the TCP/IP address space that manages the connection for the Listener  
  
- `LISTENER` statement.  Specifies the port number that the Listener will use. This statement also specifies other port-related parameters, such as backlog, time-out values, and so on.  
  
- `TRANSACTION` statement.  Defines a list of transactions that the Listener can start. It also defines whether the Implicit or Explicit connection mode is used.  
  
  The Listener uses the three previously listed parameter statements to inform TCP/IP which port to use and which transactions can be accessed through TCP/IP.  
  
  The following is a sample of an IMS-to-TCP/IP host definition:  
  
```  
TCPIP ADDRSPC=WNWTCP31  
LISTENER PORT=4000 BACKLOG=50  
TRANSACTION NAME=TRANIMPL TYPE=IMPLICIT  
TRANSACTION NAME=TRANEXPL TYPE=EXPLICIT  
  
```  
  
## See Also  
 [How to Run TI Over TCP/IP](../core/how-to-run-ti-over-tcp-ip2.md)