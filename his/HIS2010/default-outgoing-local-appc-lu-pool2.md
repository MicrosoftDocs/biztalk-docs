---
title: "Default Outgoing Local APPC LU Pool2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06910573-3609-4226-bbba-91025ddea70a
caps.latest.revision: 3
---
# Default Outgoing Local APPC LU Pool
With Host Integration Server, you can set up a pool of local APPC LUs that will be allocated dynamically for any invoking transaction program that does not specify a local LU. This feature is designed to coexist with the default local and remote LUs for users and groups, and does not override these settings.  
  
 Both of the default APPC LU features (the default outgoing local APPC LU pool and the default local and remote LUs for users and groups)  allow client computers to start a session without specifying an LU name. This helps to simplify administration by eliminating APPC configuration for client computers.  
  
 If an application begins the invoking process but does not specify a local APPC LU, Host Integration Server first tries to determine the default local APPC LU of the associated user or group (the user or group logged on at the system where the application is running). If no such LU can be substituted, Host Integration Server attempts to assign an LU from the default pool of outgoing local APPC LUs. If no LUs are available from the default pool, the attempt to begin the invoking process is rejected.  
  
 The default outgoing local APPC LU pool differs from, and should not be confused with, 3270, LUA, and downstream pools.  
  
## See Also  
 [APPC Mode Definition](../HIS2010/appc-mode-definition1.md)   
 [Implicit Incoming Remote LU and Implicit Incoming Mode](../HIS2010/implicit-incoming-remote-lu-and-implicit-incoming-mode2.md)   
 [Default Local APPC LU and the Default Remote APPC LU](../HIS2010/default-local-appc-lu-and-the-default-remote-appc-lu2.md)   
 [Single-System APPC](../HIS2010/single-system-appc1.md)