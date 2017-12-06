---
title: "AS-400 5250 Terminal Connections1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5d4c58b-8fb9-44c4-991e-41c4431864e6
caps.latest.revision: 3
author: MandiOhlinger
---
# AS/400 5250 Terminal Connections
Host Integration Server computers provide access to AS/400 computers by emulating 5250 display terminals. A 5250 user communicating with an AS/400 must use a pair of APPC LUs (LU 6.2). This pair contains a local LU and a remote LU (as viewed by the Host Integration Server computer). Together, these two LUs (along with the mode that they use) contain the configuration information needed for establishing a session with the AS/400 computer.  
  
 A local APPC LU can be either independent or dependent. An independent local APPC LU can communicate directly with a peer system. A dependent APPC LU requires the support of a mainframe. These are described in more detail in later sections.  
  
 The 5250 user can share this pair of LUs with many other users at the same time, or the 5250 user can have exclusive possession of the LUs (depending on the Host Integration Server configuration). In addition, Host Integration Server computers can be configured so that users can start 5250 emulation sessions without knowing the names of LUs to request. This configuration is accomplished with the use of default LUs that are specified for each 5250 user or for groups of users.  
  
 You can configure 5250 terminal emulation using the wizard provided with Host Integration Server. Available under the **Tools** menu, the wizard takes you through each step of configuring AS/400 connection properties, creating remote APPC LUs linked to your AS/400 computer, and, if necessary, creating local APPC LUs.  
  
 In addition to wizards, several features of Host Integration Server can simplify configuration for APPC:  
  
-   [Implicit Incoming Remote LU and Implicit Incoming Mode](../core/implicit-incoming-remote-lu-and-implicit-incoming-mode.md), which allow Host Integration Server to accept requests that arrive by unrecognized remote LUs and modes.  
  
-   [Default Local APPC LU and the Default Remote APPC LU](../core/default-local-appc-lu-and-the-default-remote-appc-lu.md), which allow LU aliases to be associated with user or group names, simplifying the routing of incoming requests and the configuration of client systems.  
  
-   [Default Outgoing Local APPC LU Pool](../core/default-outgoing-local-appc-lu-pool.md), which allows LUs to be allocated dynamically to any invoking TP (transaction program) that does not specify a local LU.  
  
-   [Single-System APPC](../core/single-system-appc.md), which allows two local APPC LUs residing on the same server to communicate with each other using defined parameters.  
  
## See Also  
 [Host Integration Server 5250 (AS/400) Connectivity](../core/host-integration-server-5250-as-400-connectivity.md)   
 [APPC](../core/appc.md)