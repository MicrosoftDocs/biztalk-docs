---
description: "Learn more about: Client to Host Integration Server Problems"
title: "Client to Host Integration Server Problems"
ms.custom: ""
ms.date: "01/26/2024"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Client to Host Integration Server Problems
When you are troubleshooting an issue between a client and the HIS server computer, the first step is to verify that the client workstation can connect to other network resources on the Windows Server where the Host Integration Server is installed. If you can't map a network drive at the workstation, you should troubleshoot this problem as a workstation to Windows Server issue.
  
 If you can map a network drive at the workstation but cannot get an emulation session, you should determine what protocol is being used. Host Integration Server supports client connections over any of the network protocols. In addition, TCP/IP connections may be either named pipes or sockets. If you are unsure, run Host Integration Server Setup or Configuration at the client. If TCP/IP has been selected, the connection is sockets-based.  
  
 If the protocol chosen is "Microsoft Networking," Named Pipes is being used. Depending on which protocols are installed, "Microsoft Networking" will use NetBEUI or TCP/IP.  
  
 A common problem preventing workstations from connecting to the Host Integration Server over TCP/IP is failed NetBIOS name resolution. If you can ping the TCP/IP address of the server, but not its NetBIOS name, then you are probably having trouble with WINS or an LMHOSTS file. Configure the client for the IP address rather than the NetBIOS name.  
  
 If TCP/IP is being used, the IP address should be entered in the "Primary Server" field rather than the NetBIOS name.  
  
 5250 emulation utilizes LU type 6.2 on the IBM i server. Often, an error message on the client will include return codes.
