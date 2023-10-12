---
description: "Learn more about: LUA_SPECIFIC.SLI_OPEN"
title: "LUA_SPECIFIC.SLI_OPEN1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# LUA_SPECIFIC.SLI_OPEN
The following structure shows the **SLI_OPEN** fields of the **LUA SPECIFIC** union member for the [SLI_OPEN](../core/sli-open2.md) verb.  
  
```  
struct SLI_OPEN {  
    unsigned char lua_init_type;  
    unsigned char lua_resv65;  
    unsigned short lua_wait;  
    struct LUA_EXT_ENTRY lua_open_extension[3];  
    unsigned char lua_ending_delim;  
} SLI_OPEN;  
```  
  
## Remarks  
  
## Members  
 *lua_init_type*  
 Type of session initiation.  
  
 *lua_resv65*  
 Reserved field.  
  
 *lua_wait*  
 Secondary retry wait time.  
  
 *lua_open_extension*  
 Supplied parameter. Specifies any user-supplied dynamic-link libraries (DLLs) used to process specific LUA messages.  
  
 *lua_ending_delim*  
 Extension list delimiter.
