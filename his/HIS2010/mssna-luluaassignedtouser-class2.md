---
title: "MsSna_LuLuaAssignedToUser Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 338530fd-2161-446e-861a-c56f9b2103aa
caps.latest.revision: 4
---
# MsSna_LuLuaAssignedToUser Class
Associates an LUA LU with a user.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuLuaAssignedToUser : MsSna_Lu3270AssignedToUser  
{  
   MsSna_LuLua ref PathToLuLua;  
   MsSna_ConfiguredUser ref PathToUser;  
};  
```  
  
## Properties  
 **MsSna_LuLua**  
 Data Type: **ref PathToLuLua** Qualifiers: **Key** Access Type: Read-Only  
  
 The LUA LU to associate with.  
  
 **MsSna_ConfiguredUser**  
 Data Type: **ref PathToUser** Qualifiers: **Key** Access Type: Read-Only  
  
 The user to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../HIS2010/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)