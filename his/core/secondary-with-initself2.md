---
description: "Learn more about: Secondary with INITSELF"
title: "Secondary with INITSELF2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Secondary with INITSELF
To initialize a session by having the secondary issue an INITSELF command, set **open.lua_init_type** to LUA_INIT_TYPE_SEC_IS. When this type of session initialization is chosen, the application has to format and provide the INITSELF command. The address of the INITSELF command is specified by **lua_data_ptr**. The actual length of the INITSELF command is specified by **lua_data_length**.
