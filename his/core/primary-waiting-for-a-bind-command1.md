---
description: "Learn more about: Primary Waiting for a BIND Command"
title: "Primary Waiting for a BIND Command1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Primary Waiting for a BIND Command
To initialize a session by having the secondary wait for the primary to issue a BIND and SDT, set **open.lua_init_type** to LUA_INIT_TYPE_PRIM. Until the host begins a session with the Windows logical unit application (LUA) application using the BIND command followed by an SDT command, the **SLI_OPEN** issued stays IN_PROGRESS.
