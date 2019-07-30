---
title: "Configuring CICS for TCP-IP2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 031cd7a3-2958-41cc-9b29-ba97c077097d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Configuring CICS for TCP/IP
## CICS TCP/IP Platform Requirements  
 TCP/IP version 3R2  
  
 CICS version 3.3 or later  
  
## Connections to CICS using TCP/IP  
 CICS uses the IBM-supplied Concurrent Listener (program EZACIC02, transaction ID CSKL) to establish an interaction with TCP/IP. The Listener is a transaction that automatically starts when CICS TCP/IP is started and enabled. When the Listener starts, it obtains a socket on which it can "listen" for connection requests from TCP/IP. The Listener binds the socket to a specified port, and then waits for a client request on that port. TCP/IP maintains a relationship of a port number to a CICS job. When a client makes a request on a port associated with CICS, TCP/IP forwards the connection request to the Listener in that CICS job.  
  
 For additional details about the CICS MS LINK communication model, see CICS MS LINK (TCP/IP).  
  
## TCP/IP-to-CICS Configuration  
 A TCP/IP port number is associated with a CICS region in the TCP/IP profile data set (hlq.PROFILE.TCPIP). The port statement is used to define this relationship. For example, the following is a port statement that associates port 3000 with CICS region CICSRG:  
  
```  
3000 TCP CICSRG  
  
```  
  
## CICS-to-TCP/IP Configuration  
 The following sample host definition shows configuration parameters for CICS-to-TCP using the EZAC transaction:  
  
```  
EZAC,DEFINE  
ENTER ONE OF THE FOLLOWING  
CICS         ===> yes                  Enter Yes|No  
LISTENER     ===>                      Enter Yes|No  
EZAC,DEFINE,CICS  
ENTER ALL FIELDS  
APPLID       ===> CICSRG               APPLID of CICS System  
EZAC,DEFINE,CICS  
OVERTYPE TO ENTER  
APPLID       ===> CICSRG               APPLID of CICS System  
TCPADDR      ===> TCPIP                Name of TCP Address Space  
NTASKS       ===> 020                  Number of Reusable Tasks  
DPRTY        ===> 000                  DPRTY value for ATTACH  
CACHMIN      ===> 015                  Minimum Refresh Time for Cache  
CACHMAX      ===> 030                  Maximum Refresh Time for Cache  
CACHRES      ===> 010                  Maximum number of Resolvers  
ERRORTD      ===> CSMT                 TD Queue for Error Messages  
  
```  
  
 The following sample host definition shows configuration parameters for the CICS Concurrent Listener using the EZAC transaction:  
  
```  
EZAC,DEFINE  
ENTER ONE OF THE FOLLOWING  
CICS         ===>                      Enter Yes|No  
LISTENER     ===> yes                  Enter Yes|No  
EZAC,DEFINE,LISTENER  
ENTER ALL FIELDS  
APPLID       ===> CICSRG               APPLID of CICS System  
NAME         ===> CSKL                 TRANSACTION NAME OF LISTENER  
EZAC,DEFINE,LISTENER  
OVERTYPE TO ENTER  
APPLID       ===> CICSRG               APPLID of CICS System  
TRANID       ===> CSKL                 Transaction Name of Listener  
PORT         ===> 03000                Port Number of Listener  
IMMEDIATE    ===> YES                  Immediate Startup   Yes|No  
BACKLOG      ===> 010                  Backlog Value for Listener  
NUMSOCK      ===> 050                  Number of Sockets in Listener  
MINMSGL      ===> 004                  Minimum Message Length  
ACCTIME      ===> 060                  Timeout Value for ACCEPT  
GIVTIME      ===> 030                  Timeout Value for GIVESOCKET  
REATIME      ===> 000                  Timeout Value for READ  
FASTRD       ===> YES                  Read Immediately    Yes|No  
TRANTRN      ===> YES                  Translate TRNID     Yes|No  
TRANUSR      ===> YES                  Translate User Data Yes|No  
SECEXIT      ===>                      Name of Security Exit  
  
```  
  
 Before you attempt to use the TCP/IP connection, do the following:  
  
-   Verify that you have a TCP address space running on the host. (You should be able to PING the host at its IP address or DNS name.) Record the IP address; you will need to know it later when you use Transaction Integrator (TI) Manager to define a TCP/IP remote environment for the CICS region.  
  
-   Check that the CICS region supports TCP/IP, and that the IBM-supplied Listener (program EZACIC02, transaction ID CSKL) is defined. These procedures are described in chapter 5 of *TCP/IP* *V3R2* *for* *MVS:* *CICS* *TCP/IP* *Socket* *Interface* *Guide* (IBM Document #SC31-7131). Note that this is a CICS TS version 1.2 document, but the configuration is also supported in CICS version 4.1.  
  
-   Determine the IP port number of the Listener (EZAC DISPLAY LISTENER); you will need to know it when you use TI Manager to define a TCP/IP remote environment for the CICS region.  
  
-   Start the IBM-supplied Listener (EZAO START) and check the CICS view of the Listener status (execute the CEMT INQUIRE TASK command, and verify that CSKL is running).  
  
## See Also  
 [How to Run TI Over TCP/IP](../core/how-to-run-ti-over-tcp-ip2.md)