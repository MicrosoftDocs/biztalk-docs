---
description: "Learn more about: LUA_SPECIFIC"
title: "LUA_SPECIFIC1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# LUA_SPECIFIC
The following union shows the specific data structure that is included for functions that use the **LUA_SPECIFIC** part of a verb control block. The only logical unit application (LUA) verbs that use this union are [RUI_BID](./rui-bid1.md),[SLI_BID](./sli-bid2.md),[SLI_OPEN](../core/sli-open2.md), and [SLI_SEND](./sli-send2.md).  
  
```  
union LUA_SPECIFIC {  
    struct SLI_OPEN open;  
    unsigned char lua_sequence_number[2];  
    unsigned char lua_peek_data[12];  
} LUA_SPECIFIC;  
```  
  
## Remarks  
  
## Members  
 *open*  
 The union member of **LUA_SPECIFIC** used by the **SLI_OPEN** verb.  
  
 *lua_sequence_number*  
 The union member of **LUA_SPECIFIC** used by the **SLI_SEND** verb. Returned parameter. Sequence number of the RU to the host.  
  
 *lua_peek_data*  
 The union member of **LUA_SPECIFIC** used by the **RUI_BID** and **SLI_BID** verbs. Returned parameter. Contains up to 12 bytes of the data waiting to be read.  
  
 This section contains the following topics:  
  
 [LUA_SPECIFIC.SLI_OPEN](../core/lua-specific-sli-open1.md)  
  
 [LUA_EXT_ENTRY](../core/lua-ext-entry2.md)
