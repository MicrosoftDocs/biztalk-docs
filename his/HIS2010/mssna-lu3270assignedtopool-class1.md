---
title: "MsSna_Lu3270AssignedToPool Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e7234ae-7e1c-4506-a2ff-fafe44b6c3f0
caps.latest.revision: 4
---
# MsSna_Lu3270AssignedToPool Class
Associates a 3270 LU with a pool.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_Lu3270AssignedToPool : MsSna_Association   
{  
   MsSna_Pool ref PathToPool3270;  
   MsSna_Lu3270 ref PathToLu3270;  
};  
```  
  
## Properties  
 **MsSna_Pool**  
 Data Type: **ref PathToPool3270** Qualifiers: **Key** Access Type: Read-Only  
  
 The pool to associate with.  
  
 **MsSna_Lu3270**  
 Data Type: **ref PathToLu3270** Qualifiers: **Key** Access Type: Read-Only  
  
 The 3270 LU to associate with.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../HIS2010/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)