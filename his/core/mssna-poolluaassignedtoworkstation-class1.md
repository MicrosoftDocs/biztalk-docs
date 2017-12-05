---
title: "MsSna_PoolLuaAssignedToWorkstation Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3a4820e-74f8-45c5-ac17-8f3d3401dc03
caps.latest.revision: 4
---
# MsSna_PoolLuaAssignedToWorkstation Class
Associates an LUA pool with a workstation.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_PoolLuaAssignedToWorkstation : MsSna_PoolAssignedToWorkstation  
{  
   MsSna_PoolLua ref PathToPoolLua;  
   MsSna_Workstation ref PathToWorkstation;  
};  
```  
  
## Properties  
 **MsSna_PoolLua**  
 Data Type: **ref PathToPoolLua** Qualifiers: **Key** Access Type: Read-Only  
  
 The LUA pool to associate with.  
  
 **MsSna_Workstation**  
 Data Type: **ref PathToWorkstation** Qualifiers: **Key** Access Type: Read-Only  
  
 The workstation to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)