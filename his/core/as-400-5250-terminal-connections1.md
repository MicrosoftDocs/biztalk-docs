---
title: 5250 terminal connections for IBM System i
description: Learn more about terminal connections for IBM System i 5250.
ms.service: host-integration-server
ms.topic: conceptual
ms.date: 11/23/2023
---

# Terminal connections for IBM System i 5250

Host Integration Server computers provide access to IBM System i computers by emulating 5250 display terminals. A 5250 user communicating with an IBM System i must use a pair of APPC LUs (LU 6.2). This pair contains a local LU and a remote LU (as viewed by the Host Integration Server computer). Together, these two LUs (along with the mode that they use) contain the configuration information needed for establishing a session with the IBM System i computer.

A local APPC LU can be either independent or dependent. An independent local APPC LU can communicate directly with a peer system. A dependent APPC LU requires the support of a mainframe. These are described in more detail in later sections.  
  
The 5250 user can share this pair of LUs with many other users at the same time, or the 5250 user can have exclusive possession of the LUs (depending on the Host Integration Server configuration). In addition, Host Integration Server computers can be configured so that users can start 5250 emulation sessions without knowing the names of LUs to request. This configuration is accomplished with the use of default LUs that are specified for each 5250 user or for groups of users.  
  
You can configure 5250 terminal emulation using the wizard provided with Host Integration Server. Available under the **Tools** menu, the wizard takes you through each step of configuring IBM System i connection properties, creating remote APPC LUs linked to your IBM System i computer, and, if necessary, creating local APPC LUs.  
  
In addition to wizards, several features of Host Integration Server can simplify configuration for APPC:  

- [Implicit Incoming Remote LU and Implicit Incoming Mode](../core/implicit-incoming-remote-lu-and-implicit-incoming-mode1.md), which allow Host Integration Server to accept requests that arrive by unrecognized remote LUs and modes.  

- [Default Local APPC LU and the Default Remote APPC LU](../core/default-local-appc-lu-and-the-default-remote-appc-lu1.md), which allow LU aliases to be associated with user or group names, simplifying the routing of incoming requests and the configuration of client systems.  

- [Default Outgoing Local APPC LU Pool](../core/default-outgoing-local-appc-lu-pool1.md), which allows LUs to be allocated dynamically to any invoking TP (transaction program) that does not specify a local LU.  

- [Single-System APPC](../core/single-system-appc2.md), which allows two local APPC LUs residing on the same server to communicate with each other using defined parameters.  

## See also

[Host Integration Server 5250 (IBM System i) Connectivity](../core/host-integration-server-5250-as-400-connectivity1.md)   
[APPC](../core/appc1.md)
