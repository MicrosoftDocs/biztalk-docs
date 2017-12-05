---
title: "Programming Techniques for LUA Pools1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70ce14fc-63c5-4818-a86e-369417819c0c
caps.latest.revision: 3
---
# Programming Techniques for LUA Pools
When working with a logical unit application (LUA) LU pool, specify the pool name at the beginning of the conversation and then use the **lua_sid** member (not the pool name) with subsequent calls. This is necessary because the **lua_sid** member is a unique identifier, but the pool name is not, because a pool is designed to supply LUs for multiple conversations.  
  
 When using [RUI_INIT](../HIS2010/rui-init2.md) or [SLI_OPEN](../HIS2010/sli-open1.md) with an LUA pool, specify the pool name with the **lua_luname** member. For subsequent calls in the same conversation, use the **lua_sid** member returned from **RUI_INIT** or **SLI_OPEN** to specify the conversation.  
  
> [!NOTE]
>  On completion of RUI_INIT or SLI_OPEN, the lua_luname member contains the actual name of the LU used. This allows you to create code for a display for the user, showing the actual LU name used in a particular conversation.