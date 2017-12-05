---
title: "MsSna_LuPrintAssignedToWorkstation Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 32f7bfd4-203c-4335-8acc-160ff14eb9a4
caps.latest.revision: 4
---
# MsSna_LuPrintAssignedToWorkstation Class
Associates a print LU with a workstation.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuPrintAssignedToWorkstation : MsSna_Lu3270AssignedToWorkstation  
{  
   MsSna_LuPrint ref PathToLuPrint;  
   MsSna_Workstation ref PathToWorkstation;  
};  
```  
  
## Properties  
 **MsSna_LuPrint**  
 Data Type: **ref PathToLuPrint** Qualifiers: **Key** Access Type: Read-Only  
  
 The print LU to associate with.  
  
 **MsSna_Workstation**  
 Data Type: **ref PathToWorkstation** Qualifiers: **Key** Access Type: Read-Only  
  
 The user to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)