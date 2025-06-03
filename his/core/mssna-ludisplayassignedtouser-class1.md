---
description: "Learn more about: MsSna_LuDisplayAssignedToUser Class"
title: "MsSna_LuDisplayAssignedToUser Class1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSna_LuDisplayAssignedToUser Class
Associates a display LU with a user.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuDisplayAssignedToUser : MsSna_Lu3270AssignedToUser  
{  
   MsSna_LuDisplay ref PathToLuDisplay;  
   MsSna_ConfiguredUser ref PathToUser;  
};  
```  
  
## Properties  
 **MsSna_LuDisplay**  
 Data Type: **ref PathToLuDisplay** Qualifiers: **Key** Access Type: Read-Only  
  
 The display LU to associate with.  
  
 **MsSna_ConfiguredUser**  
 Data Type: **ref PathToUser** Qualifiers: **Key** Access Type: Read-Only  
  
 The user to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
