---
title: "LUA_EXT_ENTRY1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 703f8c04-f156-45f5-9063-7e912709d136
caps.latest.revision: 3
---
# LUA_EXT_ENTRY
The following structure shows the **LUA_EXT_ENTRY** fields of the [LUA SPECIFIC.SLI_OPEN](../HIS2010/lua-specific-sli-open2.md) union member for the [SLI_OPEN](../HIS2010/sli-open1.md) verb.  
  
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