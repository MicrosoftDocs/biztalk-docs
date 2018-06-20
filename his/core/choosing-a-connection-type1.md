---
title: "Choosing a Connection Type1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e780e5f3-1632-434d-91a0-4e517b50ebab
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Choosing a Connection Type
A [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer can use any of the types of connections described in this section. To choose a connection type for your servers, you should first contact the host administrator and find out the type of connection available to the mainframe or AS/400. If more than one type is available, choose a type based on comparisons of cost and speed.  
  
 For demonstration purposes, you can install the [Demo SDLC link service](../core/demo-sdlc-link-service-linkcfg-1.md), which receives messages from Host Integration Server and responds to them itself from a prerecorded script.  
  
 The various adapters in a computer must be configured to work together so that there are no interrupt, port address, or direct memory access (DMA) conflicts. When you install a new adapter in your computer, you may need to study the configuration of the new and old adapters to make sure that there are no conflicts.  
  
 The following connection types are available:  
  
- 802.2 Data Link Control (DLC 802.2)  
  
   Token ring, Ethernet, or Fiber Distributed Data Interface (FDDI) connections use the IEEE 802.2 protocol. With a mainframe, an 802.2 connection goes to a 37*xx* front-end processor (FEP) or a 3174 communications controller (or, rarely, to an adapter in the mainframe). With an AS/400 system, an 802.2 connection goes directly to the AS/400.  
  
   These connections are generally faster than other connections, except for channel connections. The following table provides details.  
  
  |Type of 802.2 connection|Common speeds|  
  |------------------------------|-------------------|  
  |Token ring|4 megabits per second (Mbps) or 16 Mbps.|  
  |Ethernet/Fast Ethernet|10–100 Mbps.|  
  |FDDI|100 Mbps (or more); however, the FDDI line communicates through a front-end processor that is channel-attached to the mainframe, and this may limit the overall speed of communications.|  
  
   DLC 802.2 also has certain limitations. The 802.2 link service cannot support more than one 802.2 connection to the same MAC address and destination SAP (that is, to the same host) at the same time, whether the connections originate from the local or a remote SNA Server computer. The 802.2 protocol specification does not permit two distinct connections to have the same Source MAC, Source SAP, Destination MAC, and Destination SAP. The 802.2 link service is bound to a particular LAN adapter and source SAP value, and therefore uses the same source MAC and SAP for all connections. To support multiple connections, you can:  
  
  - Connect to different network adapters on the host.  
  
  - Configure multiple 802.2 link services, all bound to the same LAN adapter but specifying different source SAPs.  
  
  - Support multiple connections to a given host through the same 802.2 link service. Verify that the host is configured to accept 802.2 connections on multiple SAPs. This can be configured to mainframe FEPs (but is rarely used). AS/400s support multiple SAPs by default. These SAP values are configured as the remote SAP value on the Host Integration Server connection, which is configured on the Host Integration Server computer using the distributed link service.  
  
    This limitation applies to connections based on the 802.2 link service in general.  
  
    When you make an 802.2 link service available to distributed link service on other Host Integration Server computers, it cannot be used by the local Host Integration Server computer, and is not visible in SNA Manager Console.  
  
- Synchronous Data Link Control (SDLC)  
  
   SDLC uses a standard phone line, which can be leased or switched and can be point-to-point or multi-drop. An SDLC line is used with a modem or other type of data circuit -terminating equipment (DCE) at each end. With a mainframe, an SDLC line travels through a modem or other DCE to a 37*xx* front-end processor (FEP), 3174 communications controller, or integrated synchronous adapter. With an AS/400 system, an SDLC line goes through a modem or other DCE, and then directly to the AS/400.  
  
   An SDLC connection is slower than an 802.2 or channel connection. Common speeds for SDLC connections are listed in the following table.  
  
  |Type of transmission|Common speeds|  
  |--------------------------|-------------------|  
  |Analog (conventional phone line)|9600–56000 bits per second|  
  |Digital Data System (DDS)|56 kilobits per second (kbps)  (sometimes 64 kbps)|  
  |Integrated Services Digital Network (ISDN)|56 kbps (can be more)|  
  |T1 carrier system (digital)|1.544 megabits per second (Mbps)|  
  |E1 carrier system (digital)|2.048 Mbps|  
  
   SDLC connections are useful for wide-area connections between geographically disparate locations, or when bandwidth and usage requirements are low. Because of these factors, SDLC is ideally suited for branch-type deployment strategies.  
  
   Host Integration Server supports SDLC connections using the link support that is included with it or through an SDLC link service available through various third-party vendors. Not all supported SDLC adapters support all link speeds listed in preceding table.  
  
- Distributed Link Service  
  
   The distributed link service feature provides a method for a Host Integration Server computer to connect to a host using a link service installed on a different Host Integration Server computer. The network connecting SNA Server computers need not support any SNA link level protocol such as DLC 802.2 or SDLC.  
  
   The distributed link service is configured in two parts: by installing the distributed link service on one SNA Server computer and by marking a real link service on another computer as distributable. The distributed link service acts as a proxy for sharing the distributable link service. It supports load balancing across multiple, distributed link services. It also supports hot backup because the distributed link service can select alternate remote servers when a remote link fails. It allows a branch SNA Server computer to connect to the host over a wide area network (WAN). This supports only routable internetworking protocols such as TCP/IP, rather than requiring an SNA WAN protocol such as SDLC or bridged DLC.  
  
   Distributed link services provide the following benefits:  
  
  - The branch-based Host Integration Server computers provide split-stack SNA gateway service for local client computers, simplifying configuration of the client computers. This conserves PUs and concentrates traffic on behalf of several client computers, which saves valuable network bandwidth.  
  
  - The branch-based Host Integration Server computer communicates with the central-site Host Integration Server computers through a native TCP/IP connection, which eliminates DLC 802.2 time-out problems associated with traditional SNA encapsulation methods.  
  
  - Because the central site servers provide the equivalent of PU pass-through service for the branch-based servers, the host operator sees each branch-based server as a PU and can manage the branches through standard NetView alerts and RunCmds.  
  
  - The branch-based servers can connect to the host through multiple centralized servers, load-balancing among the multiple central-site servers at connect time.  
  
  - Should a central-site server fail for any reason, the branch-based servers will automatically establish a new connection through an alternate centralized server for hot backup.  
  
  - Should the WAN fail for any reason, the branch-based Host Integration Server computers can be configured to connect to the host through a direct dial-up SDLC connection as a backup that will be activated automatically upon the host connection failure. It is actually activated upon the first request after a failure.  
  
  - The routers at the branches only need to route TCP/IP, which provides for simplicity of WAN management and cost savings.  
  
  - Because the branch-based servers rely on WAN services provided by the leading networking vendors, the distributed link service will work over all existing and future WAN technologies, including leased lines, X.25, frame relay, and ATM networks.  
  
  - Unlike other native TCP/IP solutions such as TN3270, the distributed link service is not limited in SNA functionality. Each branch-based Host Integration Server computer provides full SNA access for the local personal computers, including PU 2.0, PU 2.1, and APPN LEN service, as well as LU 0, LU 1, LU 2, LU 3, and LU 6.2 support. Both mainframe and AS/400 access are supported.  
  
    By default, when you make a link service available to distributed link service on other servers, it will permit a connection from distributed link service running on any remote server that is configured to connect to it. This is similar to the level of access control permitted by traditional pass-through gateways. Any downstream device that is configured for the correct MAC address can use the gateway.  
  
    However, you can restrict access to the distributed link service, requiring the remote distributed link service to provide a valid Windows server username and password. The procedure requires coordination between the upstream and remote servers.  
  
## See Also  
 [SNA Service](../core/sna-service2.md)