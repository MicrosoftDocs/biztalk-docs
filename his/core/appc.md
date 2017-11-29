---
title: "APPC1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b04ce26b-ee2e-49ee-9a22-94737763af57
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# APPC
Advanced Program-to-Program Communications (APPC), or LU 6.2, provides a transport vehicle for programs on peer systems to communicate with each other over the SNA network. APPC is software that enables high-speed communications between programs on different computers.  
  
 APPC is a change from the terminal-to-host connections used in many 3270 systems. APPC moves to a distributed transaction programming environment by providing a common set of SNA protocols that brings compatibility at a program communications level.  
  
 APPC serves as translator between application programs and the network. When applications on one computer pass information to the APPC software, APPC translates the information and passes it to a network interface. APPC translates the information back into its original format and passes it to the corresponding partner application. APPC can be used across any of the standard types of connections supported by SNA and is not tied to any particular physical connection.  
  
 APPC generally uses a local APPC LU (LU 6.2) and one or more remote APPC LUs. A local APPC LU can be independent or dependent. In full peer-oriented APPN networks, typically implemented in an AS/400 environment or under the most modern evolution of mainframe technology, the independent APPC model applies. Dependent APPC is used in older mainframe networks, and its functions are reduced.  
  
 Local and remote APPC LUs work together in pairs. The local APPC LU is assigned to a server (unlike other LU types, which are assigned to connections). The remote APPC LU is assigned to the connection. Host Integration Server uses dynamic partnering to create any possible LU partnership on demand when local and remote LUs and modes recognize each other.  
  
 With dynamic APPC partnering, an administrator configures remote LUs, but does not need to partner them with local LUs. Host Integration Server will automatically partner the LUs when needed.  
  
 With dynamic APPC configuration, an administrator does not need to configure remote LUs. If a connection is designated to support dynamic APPC configuration, Host Integration Server will automatically define a remote LU and partner it with a local LU when needed.  
  
 Independent APPC provides the ability to run multiple, concurrent, parallel sessions between a single pair of LUs. Dependent APPC allows only a single session between a given pair of LUs.  
  
 Programs that use APPC are referred to as transaction programs (TPs). There are two types of TPs: those that can invoke a conversation, and those that can be invoked. A TP can provide any type of service: terminal emulation, data transfer, database query or update, and so on.  
  
 The characteristics that govern the interactions between TPs using an LU 6.2-LU 6.2 connection are determined by the mode associated with the connection. The mode can be associated in a fixed manner with a given LU, or it can be supplied by the invoking TP when a session is first initiated.  
  
## See Also  
 [Host Integration Server 5250 (AS/400) Connectivity](../core/host-integration-server-5250-as-400-connectivity.md)   
 [AS/400 5250 Terminal Connections](../core/as-400-5250-terminal-connections.md)