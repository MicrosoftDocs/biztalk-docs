---
description: "Learn more about: MsSna_PoolDisplayAssignedToWorkstation Class"
title: "MsSna_PoolDisplayAssignedToWorkstation Class1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSna_PoolDisplayAssignedToWorkstation Class
Associates a display pool with a workstation.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_PoolDisplayAssignedToWorkstation : MsSna_PoolAssignedToWorkstation  
{  
   MsSna_PoolDisplay ref PathToPoolDisplay;  
   MsSna_Workstation ref PathToWorkstation;  
};  
```  
  
## Properties  
 **MsSna_PoolDisplay**  
 Data Type: **ref PathToPoolDisplay** Qualifiers: **Key** Access Type: Read-Only  
  
 The display pool to associate with.  
  
 **MsSna_Workstation**  
 Data Type: **ref PathToWorkstation** Qualifiers: **Key** Access Type: Read-Only  
  
 The workstation to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
