---
title: "LUA_EXT_ENTRY2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2bba5da6-711a-4a72-8cce-3a7d68761edd
caps.latest.revision: 4
---
# LUA_EXT_ENTRY
The following structure shows the **LUA_EXT_ENTRY** fields of the [LUA SPECIFIC.SLI_OPEN](../core/lua-specific-sli-open.md) union member for the [SLI_OPEN](../core/sli-open.md) verb.  
  
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