---
title: "CPI-C Access2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a292c055-759a-4008-8e49-ec051a62afb6
caps.latest.revision: 3
---
# CPI-C Access
Common Programming Interface for Communications (CPI-C) provides a consistent application programming interface for network applications. CPI-C is a set of C-language routines that applications distributed across an SNA network can use to communicate as peers and exchange data to accomplish a processing task.  
  
 CPI-C programming provides a mechanism, called side information, that associates a set of parameters with a specified symbolic destination name. The CPI-C program then uses the symbolic destination name to initialize a conversation.  
  
 If you are using applications based on CPI-C, you configure one or more CPI-C symbolic destination names. A CPI-C symbolic destination name is a name assigned to a set of properties for a CPI-C conversation.  
  
 LU partners will need to recognize each other. This is accomplished using fully qualified names and LU aliases. The fully qualified name is a two-part name that identifies the remote LU. The first part of the fully qualified name is the network name and the second part is the remote LU name.  
  
 You will also need a mode name. For more information about modes, see the section [APPC Mode Definition](../core/appc-mode-definition.md) earlier in this section.  
  
 Conversation-level security requires a match between the user ID and password supplied by the invoking TP, and the user ID and password stored on the server where the remote TP resides. If the ID and password do not match, the session is not activated.  
  
## See Also  
 [Understanding Connectivity](../core/understanding-connectivity.md)