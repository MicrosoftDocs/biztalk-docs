---
title: "Command-Specific Structure of LUA VCBs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6276f593-a161-4113-8657-7c42a4ddfcbe
caps.latest.revision: 3
---
# Command-Specific Structure of LUA VCBs
The following union shows the specific data structure that is included for functions that use the **LUA_SPECIFIC** part of a verb control block. The only logical unit application (LUA) verbs that use this union are [RUI_BID](../core/rui-bid2.md),[SLI_BID](../core/sli-bid1.md),[SLI_OPEN](../core/sli-open1.md), and [SLI_SEND](../core/sli-send1.md).  
  
## Syntax  
  
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
 The union member of **LUA_SPECIFIC** used by the **SLI_SEND** verb. Returned parameter. Sequence number of the RU to the host. It contains the sequence number for either the first in the chain request unit or the only segment in the chain request unit. Note that this parameter is not byte-reversed.  
  
 *lua_peek_data*  
 The union member of **LUA_SPECIFIC** used by the **RUI_BID** and **SLI_BID** verbs. Returned parameter. Contains up to 12 bytes of the data waiting to be read. It is a preview (up to 12 bytes) of the request/response unit (RU) data waiting to be read. The **lua_data_length** parameter contains the exact length of the data peeked at.  
  
 The following topic describes command-specific parameters for **SLI_OPEN**.  
  
 This section contains:  
  
-   [SLI_OPEN VCB Structure](../core/sli-open-vcb-structure1.md)