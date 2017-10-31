---
title: "Host Integration Server Extensions1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: de2c2fc1-31fc-4c7e-a98b-4c47a1c5df09
caps.latest.revision: 3
---
# Host Integration Server Extensions
The Host Integration Server **DISPLAY** verb is compatible with the IBM ES for OS/2 version 1.0 **DISPLAY** verb. However, since IBM ES for OS/2 version 1.0 is a single-server system and Host Integration Server supports multiple-server systems, the **DISPLAY** verb has been extended to allow the user to target a specific server running Host Integration Server by which the **DISPLAY** verb will be processed.  
  
 To direct a **DISPLAY** verb at a particular server running Host Integration Server, place the ASCII string CSEXTNID, followed by the computer name of the server running Host Integration Server at the start of the buffer pointed to by **buffer_ptr**. The computer name is a 32-byte ASCII string and can be zero or padded with spaces.  
  
 Because the local node identifier is configured on a per-node basis for IBM ES for OS/2 version 1.0 and can be different for each connection in Host Integration Server, Host Integration Server also allows you to specify an optional connection name. This is an 8-byte ASCII string, which is placed after the 32-byte computer name. Again, the string can be zero or padded with spaces. The following example illustrates the CSEXTNID extension:  
  
 csextnid computername 00000000000000000000 name  
  
 If you do not specify a connection name, Host Integration Server returns information about the first connection configured for the Host Integration Server system.  
  
 If you do not specify a computer name, Host Integration Server will randomly choose a default **DISPLAY** computer and connection, unless a specific default **DISPLAY** connection has been configured on the server. These parameters can be configured with the SNA Manager or the Host Integration Server Administrator Client when using [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)]. **DISPLAY** will behave as if you specified the connection and the computer name of the server that owns the verb. For additional information about using default LUs, see [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] Help.  
  
 Host Integration Server also allows you to use **DISPLAY** to return a list of active servers. To do so, place the string CSEXTNIDCSLISTND in the **DISPLAY** buffer and set the supplied parameters **sna_global_info**, **lu62_info**, and so on, to AP_NO. The information is returned in the **DISPLAY** buffer in the following format.  
  
## Syntax  
  
```  
  
#activenodes            - 2 bytes  
  node_name 1           - 8 bytes  
  box_name 1            - 32 bytes  
  .  
  node_name m  
  box_name m  
```  
  
## Remarks  
 In the current version of Host Integration Server, **node_name** is always SNASERVR and **box_name** is the computer name of the server.