---
description: "Learn more about: MsSna_LuDisplayAssignedToWorkstation Class"
title: "MsSna_LuDisplayAssignedToWorkstation Class2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSna_LuDisplayAssignedToWorkstation Class
Associates a display LU with a workstation.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuDisplayAssignedToWorkstation : MsSna_Lu3270AssignedToWorkstation  
{  
   MsSna_LuDisplay ref PathToLuDisplay;  
   MsSna_Workstation ref PathToWorkstation;  
};  
```  
  
## Properties  
 **MsSna_LuDisplay**  
 Data Type: **ref PathToLuDisplay** Qualifiers: **Key** Access Type: Read-Only  
  
 The display LU to associate with.  
  
 **MsSna_Workstation**  
 Data Type: **ref PathToWorkstation** Qualifiers: **Key** Access Type: Read-Only  
  
 The user to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
