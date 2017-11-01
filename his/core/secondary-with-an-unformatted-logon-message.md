---
title: "Secondary with an Unformatted LOGON Message2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17e5ae34-7d99-465b-a5bf-8648aa9fb088
caps.latest.revision: 3
---
# Secondary with an Unformatted LOGON Message
To initialize a session by having the secondary issue an unformatted LOGON message, set **open.lua_init_type** to LUA_INIT_TYPE_SEC_LOG. The length of the users EBCDIC LOGON message is then specified in **lua_data_length**. The address of the users EBCDIC LOGON message length is specified by **lua_data_ptr**.