---
title: "MsSna_LuPrintAssignedToUser Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 055513d9-b61e-47b4-8d90-cd4a787b46f6
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)