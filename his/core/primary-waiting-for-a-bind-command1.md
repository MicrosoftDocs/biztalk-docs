---
title: "Primary Waiting for a BIND Command1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc17670f-58fd-489b-a287-28ee2c7ac9af
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Primary Waiting for a BIND Command
To initialize a session by having the secondary wait for the primary to issue a BIND and SDT, set **open.lua_init_type** to LUA_INIT_TYPE_PRIM. Until the host begins a session with the Windows logical unit application (LUA) application using the BIND command followed by an SDT command, the **SLI_OPEN** issued stays IN_PROGRESS.