---
title: "MsSna_LuDisplayAssignedToUser Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b8d4815-61de-4c87-b52b-18a5a45b2e26
caps.latest.revision: 4
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)