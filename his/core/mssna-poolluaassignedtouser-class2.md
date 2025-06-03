---
description: "Learn more about: MsSna_PoolLuaAssignedToUser Class"
title: "MsSna_PoolLuaAssignedToUser Class2"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
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
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
