---
title: "Secondary with an Unformatted LOGON Message1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5a1ab5c-4b83-4462-a070-fbeec03540d4
caps.latest.revision: 3
---
# Secondary with an Unformatted LOGON Message
To initialize a session by having the secondary issue an unformatted LOGON message, set **open.lua_init_type** to LUA_INIT_TYPE_SEC_LOG. The length of the users EBCDIC LOGON message is then specified in **lua_data_length**. The address of the users EBCDIC LOGON message length is specified by **lua_data_ptr**.