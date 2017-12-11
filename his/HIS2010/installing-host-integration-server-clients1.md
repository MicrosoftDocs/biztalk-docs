---
title: "Installing Host Integration Server Clients1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa76d829-16f3-4501-83f4-b2a4d069f183
caps.latest.revision: 5
---
# Installing Host Integration Server Clients
Host Integration Server client software allows client workstations to communicate with Host Integration Server computers to access host resources. Client software is installed on each workstation using applications that communicate using any Host Integration Server programmatic interfaces. Client software is available for the following platforms:  
  
-   Windows Server 2003 R2 SP2  
  
-   Windows Vista SP2  
  
-   Windows 7  
  
-   Windows Server 2008 SP2  
  
-   Windows Server 2008 R2  
  
 The fastest Host Integration Server client/server network interface is TCP/IP, although you can use other local area network (LAN) protocols such as Microsoft Networking (Named Pipes) if your LAN supports them. If you select TCP/IP or Microsoft Network, the remote installation option is recommended. Selecting "local" requires the client workstation to be on the same TCP/IP subnet as the Host Integration Server computer, which is uncommon in routed IP networks.  
  
> [!NOTE]
>  Host Integration Server client software is not required to use services such as TN3270 and TN5250. Applications, such a TN3270 emulator, communicate directly with these services using TCP/IP and do not use the Host Integration Server client/server interface.  
  
## See Also  
 [Choosing Network Protocols for Host Integration Server](../HIS2010/choosing-network-protocols-for-host-integration-server2.md)   
 [Choosing Server/Server Network Protocols](../HIS2010/choosing-server-server-network-protocols1.md)   
 [Choosing Client/Server Network Protocols](../HIS2010/choosing-client-server-network-protocols1.md)   
 [Connecting Servers](../HIS2010/connecting-servers1.md)