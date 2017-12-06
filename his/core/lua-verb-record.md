---
title: "LUA_VERB_RECORD2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7bb0ed1e-0438-48f7-96f6-0df779a6ae7f
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
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
  
 To access parameters in the specific part of the VCB, you need to include the union member name **specific.** For example, when issuing [RUI_BID](../Topic/RUI_BID2.md) using a verb record structure named **Lua_Verb**, you access its **lua_peek_data** member as **Lua_Verb.specific.lua_peek_data**.  
  
 For a complete listing of the structures and related values in the LUA VCB, see [LUA Verb Control Blocks](../Topic/LUA%20Verb%20Control%20Blocks1.md).