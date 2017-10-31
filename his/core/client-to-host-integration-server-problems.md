---
title: "Client to Host Integration Server Problems2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5eb7f3ac-3dd9-44f1-bb70-cd32dd087934
caps.latest.revision: 4
---
# Client to Host Integration Server Problems
When you are troubleshooting an issue between the workstation and the HIS server computer, the first step is to verify that the client workstation computer can connect to other network resources on the Windows 2008 Server that has Host Integration Server installed. If you cannot map a network drive at the workstation, then you should troubleshoot this problem as a workstation to Windows 2008 Server issue.  
  
 If you can map a network drive at the workstation but cannot get an emulation session, you should determine what protocol is being used. Host Integration Server supports client connections over any of the network protocols. In addition, TCP/IP connections may be either named pipes or sockets. If you are unsure, run Host Integration Server Setup or Configuration at the client. If TCP/IP has been selected, the connection is sockets-based.  
  
 If the protocol chosen is "Microsoft Networking," Named Pipes is being used. Depending on which protocols are installed, "Microsoft Networking" will use NetBEUI or TCP/IP.  
  
 A common problem preventing workstations from connecting to the Host Integration Server over TCP/IP is failed NetBIOS name resolution. If you can ping the TCP/IP address of the server, but not its NetBIOS name, then you are probably having trouble with WINS or an LMHOSTS file. Configure the client for the IP address rather than the NetBIOS name.  
  
 If TCP/IP is being used, the IP address should be entered in the "Primary Server" field rather than the NetBIOS name.  
  
 5250 emulation utilizes LU type 6.2 on the AS/400. Often, an error message on the client will include return codes.