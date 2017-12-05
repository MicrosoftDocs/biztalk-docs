---
title: "MsSna_LuDisplayAssignedToWorkstation Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2545dcd-da90-42b7-a6e6-7954daba2156
caps.latest.revision: 4
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)