---
title: "MsSna_LuPrintAssignedToUser Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb620856-3191-484d-97a5-ae4b9ab2c51d
caps.latest.revision: 4
---
# MsSna_LuPrintAssignedToUser Class
Associates a print LU with a user.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuPrintAssignedToUser : MsSna_Lu3270AssignedToUser  
{  
   MsSna_LuPrint ref PathToLuPrint;  
   MsSna_ConfiguredUser ref PathToUser;  
};  
```  
  
## Properties  
 **MsSna_LuPrint**  
 Data Type: **ref PathToLuPrint** Qualifiers: **Key** Access Type: Read-Only  
  
 The print LU to associate with.  
  
 **MsSna_ConfiguredUser**  
 Data Type: **ref PathToUser** Qualifiers: **Key** Access Type: Read-Only  
  
 The user to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)