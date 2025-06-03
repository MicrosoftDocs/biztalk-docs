---
description: "Learn more about: MsSna_LuLuaAssignedToWorkstation Class"
title: "MsSna_LuLuaAssignedToWorkstation Class2"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSna_LuLuaAssignedToWorkstation Class
Associates an LUA LU with a workstation.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuLuaAssignedToWorkstation : MsSna_Lu3270AssignedToWorkstation  
{  
   MsSna_LuLua ref PathToLuLua;  
   MsSna_Workstation ref PathToWorkstation;  
};  
```  
  
## Properties  
 **MsSna_LuLua**  
 Data Type: **ref PathToLuLua** Qualifiers: **Key** Access Type: Read-Only  
  
 The LUA LU to associate with.  
  
 **MsSna_Workstation**  
 Data Type: **ref PathToWorkstation** Qualifiers: **Key** Access Type: Read-Only  
  
 The workstation to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
