---
title: "MsSna_LuLuaAssignedToWorkstation Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f68f1004-f1dc-4682-8615-a8b46623f85c
caps.latest.revision: 4
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../HIS2010/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)