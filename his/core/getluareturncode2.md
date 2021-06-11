---
description: "Learn more about: GetLuaReturnCode"
title: "GetLuaReturnCode2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 064c5eea-043c-4188-a9d7-042542bb9efd
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# GetLuaReturnCode
The **GetLuaReturnCode** function converts the primary and secondary return codes in the verb control block (VCB) to a printable string. This function provides a standard set of error strings for use by logical unit application (LUA) applications.  
  
## Syntax  
  
```  
  
        int WINAPI GetLuaReturnCode(   
struct LUA_COMMON FAR *vpb,    
    UINT buffer_length,            
    unsigned char FAR *buffer_addr );  
```  
  
#### Parameters  
 *vpb*  
 Supplied parameter. Specifies the address of the verb control block.  
  
 *buffer_length*  
 Supplied parameter. Specifies the length of the buffer pointed to by *buffer_addr*. The recommended length is 256.  
  
 *buffer_addr*  
 Supplied/returned parameter. Specifies the address of the buffer that will hold the formatted, null-terminated string.  
  
## Return Codes  
 0x20000001  
 The parameters are invalid; the function could not read from the specified verb control block or could not write to the specified buffer.  
  
 0x20000002  
 The specified buffer is too small.  
  
 0x20000003  
 The LUA string library LUAST32.DLL could not be loaded.  
  
## Remarks  
 The descriptive error string returned in *buffer_addr* does not terminate with a newline character (**\n**).  
  
 The descriptive error strings are contained in LUAST32.DLL and can be customized for different languages.
