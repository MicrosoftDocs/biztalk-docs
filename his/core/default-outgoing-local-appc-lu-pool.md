---
title: "Default Outgoing Local APPC LU Pool1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b653358d-5e80-4629-bd1b-9690496eb137
caps.latest.revision: 3
---
# Default Outgoing Local APPC LU Pool
With Host Integration Server, you can set up a pool of local APPC LUs that will be allocated dynamically for any invoking transaction program that does not specify a local LU. This feature is designed to coexist with the default local and remote LUs for users and groups, and does not override these settings.  
  
 Both of the default APPC LU features (the default outgoing local APPC LU pool and the default local and remote LUs for users and groups)  allow client computers to start a session without specifying an LU name. This helps to simplify administration by eliminating APPC configuration for client computers.  
  
 If an application begins the invoking process but does not specify a local APPC LU, Host Integration Server first tries to determine the default local APPC LU of the associated user or group (the user or group logged on at the system where the application is running). If no such LU can be substituted, Host Integration Server attempts to assign an LU from the default pool of outgoing local APPC LUs. If no LUs are available from the default pool, the attempt to begin the invoking process is rejected.  
  
 The default outgoing local APPC LU pool differs from, and should not be confused with, 3270, LUA, and downstream pools.  
  
## See Also  
 [APPC Mode Definition](../core/appc-mode-definition.md)   
 [Implicit Incoming Remote LU and Implicit Incoming Mode](../core/implicit-incoming-remote-lu-and-implicit-incoming-mode.md)   
 [Default Local APPC LU and the Default Remote APPC LU](../core/default-local-appc-lu-and-the-default-remote-appc-lu.md)   
 [Single-System APPC](../core/single-system-appc.md)