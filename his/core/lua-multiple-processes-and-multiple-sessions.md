---
title: "LUA Multiple Processes and Multiple Sessions1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7e6a607-2c2a-4e50-a749-d3ae36c953a7
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# LUA Multiple Processes and Multiple Sessions
Two processes cannot use the same logical unit application (LUA) session. Only the process that issues [RUI_INIT](../Topic/RUI_INIT2.md) can use the session that is started by the verb. Before another process can use LUA, it must issue **RUI_INIT** to obtain a new session. However, different threads of the same process can issue verbs for the same LUA session.  
  
 A single process can simultaneously use more than one LUA session by issuing multiple **RUI_INIT** verbs. Win32® processes support for up to 15,000 sessions for applications based on the Windows Server. Each session must use a different LU. Two or more sessions can use the same pool, but the **lua_luname** member (which is either the name of the pool or the name of an LU within the pool) must be different for each **RUI_INIT**.  
  
 Two or more instances of the same LUA application can run as different processes, but they must use different LUs. This can be done by using LU pools. The two processes can specify the same pool, but are allocated different LUs from that pool.