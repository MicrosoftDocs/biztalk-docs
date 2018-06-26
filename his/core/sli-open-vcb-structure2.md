---
title: "SLI_OPEN VCB Structure2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48a259fa-cd88-41e3-acd7-a489f8872f7f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SLI_OPEN VCB Structure
The following structure shows the **SLI_OPEN** fields of the **LUA SPECIFIC** union member for the [SLI_OPEN](../core/sli-open2.md) verb.  
  
## Syntax  
  
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
 Type of session initiation, which determines how the LU-LU session is initialized by the Windows LUA interface. The following values are valid:  
  
 lua_init_type_sec_is  
  
 Secondary-initiated and sends the INITSELF command supplied in the OPEN data buffer.  
  
 lua_init_type_sec_log  
  
 Secondary-initiated with an unformatted LOGON message in the OPEN data buffer.  
  
 lua_init_type_prim  
  
 Primary-initiated and waits on the BIND command.  
  
 lua_init_type_prim_sscp  
  
 Primary-initiated with SSCP access.  
  
 *lua_resv65*  
 Reserved field.  
  
 *lua_wait*  
 Secondary retry wait time. Specifies how many seconds the Windows LUA interface is to wait before retransmitting the INITSELF or the LOGON message after receiving one of the following:  
  
- A NOTIFY command (indicating a procedure error)  
  
- A network services procedure error message  
  
- A negative response with one of the following secondary return codes:  
  
   RESOURCE_NOT_AVAILABLE SESSION_LIMIT_EXCEEDED SESSION_SERVICE_PATH_ERROR  
  
  *lua_open_extension*  
  Supplied parameter. Specifies any user-supplied dynamic-link libraries (DLLs) used to process specific LUA messages.  
  
  *lua_ending_delim*  
  Extension list delimiter.