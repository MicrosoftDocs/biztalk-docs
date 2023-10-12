---
description: "Learn more about: LUA_EXT_ENTRY"
title: "LUA_EXT_ENTRY2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# LUA_EXT_ENTRY
The following structure shows the **LUA_EXT_ENTRY** fields of the [LUA SPECIFIC.SLI_OPEN](../core/lua-specific-sli-open1.md) union member for the [SLI_OPEN](../core/sli-open2.md) verb.  
  
```  
struct LUA_EXT_ENTRY {  
     unsigned char lua_routine_type;  
     unsigned char lua_module_name[9];  
     unsigned char lua_procedure_name[33];  
};  
```  
  
## Remarks  
  
## Members  
 *lua_routine_type*  
 Extension routine type.  
  
 *lua_module_name*  
 Extension DLL module name.  
  
 *lua_procedure_name*  
 Procedure name to call in the extension DLL module.
