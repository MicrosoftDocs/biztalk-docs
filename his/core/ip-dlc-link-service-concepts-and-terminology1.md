---
title: "IP-DLC Link Service Concepts and Terminology1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98f9dfd2-87d0-400d-af03-cade72ea3ce9
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# IP-DLC Link Service Concepts and Terminology
The following is a brief introduction to the terminology and concepts that are referred to in this section, including APPN and HPR.  
  
## Session  
 A session is a logical connection between two network accessible units (NAUs). The most common example of an NAU is a logical unit (LU) (for more information, see Logical Unit (LU) later in this topic).  
  
## Physical Unit (PU)  
 The component that manages and monitors the resources (such as attached links and adjacent link stations) associated with a node. This term applies to non-APPN nodes only.  
  
## Logical Unit (LU)  
 A logical unit (LU) is a port through which an application or end user accesses the SNA network to communicate with another application or end user. An LU may be capable of supporting many sessions with other LUs.  
  
 There are two types of LUs:  
  
-   Dependent LUs require assistance from a mainframe to establish a session with another LU. These are also sometimes referred to as old LUs.  
  
-   Independent LUs can establish a session with another LU without the assistance of a mainframe.  
  
## APPN  
 Advanced Peer-to-Peer Networking (APPN) is a network architecture that supports distributed network control. It makes networks easier to configure and use, provides centralized network management, and supports flexible connectivity.  
  
## APPN Nodes  
 APPN nodes include systems of various sizes, such as mainframes using z/OS, Solaris servers running DCLs SNAP-IX, PCs running IBM Communications Server for Windows and IBM i5/OS servers.  
  
 In an APPN network, nodes can be one of the following types:  
  
- Network Nodes (NN)  
  
- End Nodes (EN)  
  
- Branch Network Nodes (BrNN)  
  
- Low-entry networking nodes (LEN nodes)  
  
  Each node in an APPN network is connected to at least one other node in the APPN network. Where supported, CP-CP (Control Point to Control Point) sessions are established over these connections to adjacent nodes (nodes in the same network that can establish direct connections without going through a third node). CP-CP sessions are used to exchange network topology information, request the location of network resources, and manage sessions. All of the nodes in an APPN network share a common network name.  
  
  **Network Node**  
  
  A Network Node provides distributed directory and routing services for all LUs in its domain, where its domain is all directly attached End Nodes and LEN nodes that are using the services of the Network Node. The Network Node is referred to as the Network Node Server (NNS) for those directly attached End Nodes and LEN nodes.  
  
  A Network Node provides the following services:  
  
- LU-LU session services for its local LUs.  
  
- Directory searches and route selection for all LUs in its domain.  
  
- Intermediate session routing for sessions between LUs on different nodes.  
  
- Routing for Management Services (MS) data, such as alerts, between a served End Node or LEN node and an MS focal point.  
  
  **End Node**  
  
  An End Node is an end point in an APPN network. It maintains directory information only for local resources. An APPN End Node can independently establish sessions between local LUs and LUs on adjacent nodes. For sessions with LUs on nodes not directly connected to the End Node, an End Node requests routing and directory information from its Network Node Server using CP-CP sessions.  
  
  End Nodes can register their local LUs with their Network Node Server. This capability means the network operator at the Network Node Server does not have to predefine the names of all LUs on the attached End Nodes to which the Network Node provides services.  
  
  An End Node can be attached to multiple network nodes, but it can have CP-CP sessions active with only one Network Node at a time: its Network Node Server. The other Network Nodes can be used only to provide intermediate routing for the end node or as substitute Network Node servers if the main Network Node Server becomes unavailable.  
  
  An End Node can also have a direct connection to another End Node or LEN node, but CP-CP sessions are never established between the two nodes.  
  
  **LEN Node**  
  
  A LEN Node is a type 2.1 node that uses independent LU 6.2 protocols, but does not support CP-CP sessions. It can be connected to a Network Node or End Node but does not support APPN functions. The existing SNA node of Host Integration Server is a LEN node.  
  
  A Network Node can provide routing services for an attached LEN node, enabling the LEN node to participate in an APPN network without requiring links to be defined between the LEN node and all of the nodes in the APPN network.  
  
  LUs in the APPN network with which the LEN node may want to establish sessions must be defined to the LEN node as if they reside on the LEN node's Network Node server. The LEN node establishes sessions with LUs defined to be contacted through its Network Node Server. The Network Node routes the session through the APPN network to the node in the network where the LU actually resides.  
  
  LUs on the LEN node must be predefined to the Network Node that serves the LEN node. LU resources on LEN nodes (unlike those on End Nodes) cannot be registered on the Network Node Server by the LEN node.  
  
  When a LEN node's only link is to an End Node, the LEN node can communicate only with LUs on the End Node through the direct link between the two nodes. This is because an End Node cannot provide intermediate routing.  
  
  **Branch Network Node**  
  
  The Branch Network Node (BrNN) combines the functions of a Network Node and an End Node. As the name implies, a BrNN can be used to subdivide a network into a backbone network and attached branch networks. The BrNN provides the following functions:  
  
- To the backbone network, the BrNN appears as an End Node, connected to its Network Node Server (NNS) in the backbone network.  
  
- The nodes in the backbone network are not aware of the nodes within the branch, reducing the amount of topology information that must be stored.  
  
- Because the BrNN appears as an End Node, it does not receive topology information from the backbone network (topology information is transmitted only between Network Nodes) reducing the amount of network overhead traffic flowing into the branch network.The BrNN registers all resources in the branch with its NNS as though they were located on the BrNN itself. This means that the nodes in the backbone network can locate resources in the branch without having to be aware of the separate nodes in the branch.  
  
- To the branch network, the BrNN appears as a Network Node, acting as the NNS for End Nodes and LEN Nodes in the branch.  
  
## High Performance Routing  
 High Performance Routing (HPR) is an extension of the APPN architecture. HPR provides the following functions:  
  
-   Rapid Transport Protocol (RTP) minimizes processing cycles and storage requirements for routing network layer packets through intermediate nodes on a session route.  
  
-   Automatic network routing (ANR) enables APPN networks to automatically reroute sessions if a portion of the originally computed route fails.  
  
## Dependent LU Requester/Server  
 Dependent LU Requester (DLUR) function enables sessions for dependent LUs to reside on remote nodes across an APPN network, instead of requiring a direct connection to the host.  
  
 DLUR works in conjunction with Dependent LU Server (DLUS) at the host. Together, they route sessions across the network from dependent LUs in the APPN network to the DLUS host. The route to the host can span multiple nodes and can take advantage of APPN's network management, dynamic resource location, and route calculation facilities.  
  
 If the local node is a Network Node, dependent LUs on downstream computers can also use pass-through DLUR, in the same way that LUs internal to the node do, to access the host across the network.  
  
## See Also  
 [System Overview](../core/system-overview1.md)   
 [Supported Features](../core/supported-features2.md)   
 [Scalability](../core/scalability1.md)   
 [Key Limitations](../core/key-limitations2.md)