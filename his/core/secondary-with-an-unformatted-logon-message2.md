---
description: "Learn more about: Secondary with an Unformatted LOGON Message"
title: "Secondary with an Unformatted LOGON Message2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Secondary with an Unformatted LOGON Message
To initialize a session by having the secondary issue an unformatted LOGON message, set **open.lua_init_type** to LUA_INIT_TYPE_SEC_LOG. The length of the users EBCDIC LOGON message is then specified in **lua_data_length**. The address of the users EBCDIC LOGON message length is specified by **lua_data_ptr**.
