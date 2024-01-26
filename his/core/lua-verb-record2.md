---
description: "Learn more about: LUA_VERB_RECORD"
title: "LUA_VERB_RECORD2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# LUA_VERB_RECORD
The logical unit application (LUA) verb control block (VCB) structure is as follows:  
  
```  
typedef struct LUA_VERB_RECORD {  
    struct LUA_COMMON common;  
    union LUA_SPECIFIC specific;  
} LUA_VERB_RECORD;  
```  
  
## Remarks  
 To access parameters in the common part of the VCB, you need to include the structure member name **common**. For example, when using a verb record structure named **Lua_Verb**, you access its **lua_prim_rc** member as **Lua_Verb.common.lua_prim_rc**.  
  
 To access parameters in the specific part of the VCB, you need to include the union member name **specific.** For example, when issuing [RUI_BID](./rui-bid1.md) using a verb record structure named **Lua_Verb**, you access its **lua_peek_data** member as **Lua_Verb.specific.lua_peek_data**.  
  
 For a complete listing of the structures and related values in the LUA VCB, see [LUA Verb Control Blocks](./lua-verb-control-blocks2.md).
