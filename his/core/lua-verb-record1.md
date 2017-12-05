---
title: "LUA_VERB_RECORD1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b96fa18e-bc0c-4880-81ce-09ae79111c5b
caps.latest.revision: 3
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
  
 To access parameters in the specific part of the VCB, you need to include the union member name **specific.** For example, when issuing [RUI_BID](../core/rui-bid2.md) using a verb record structure named **Lua_Verb**, you access its **lua_peek_data** member as **Lua_Verb.specific.lua_peek_data**.  
  
 For a complete listing of the structures and related values in the LUA VCB, see [LUA Verb Control Blocks](../core/lua-verb-control-blocks1.md).