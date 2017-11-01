---
title: "MsSna_PoolLuaAssignedToUser Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91c14ccb-34a6-42ac-a046-b69a09a76cd4
caps.latest.revision: 4
---
# MsSna_PoolLuaAssignedToUser Class
Associates a pool LUA with a user.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_PoolLuaAssignedToUser : MsSna_PoolAssignedToUser  
{  
   MsSna_PoolLua ref PathToPoolLua;  
   MsSna_ConfiguredUser ref PathToUser;  
};  
```  
  
## Properties  
 **MsSna_PoolLua**  
 Data Type: **ref PathToPoolLua** Qualifiers: **Key** Access Type: Read-Only  
  
 The pool LUA to associate with.  
  
 **MsSna_ConfiguredUser**  
 Data Type: **ref PathToUser** Qualifiers: **Key** Access Type: Read-Only  
  
 The user to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)