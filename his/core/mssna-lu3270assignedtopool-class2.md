---
description: "Learn more about: MsSna_Lu3270AssignedToPool Class"
title: "MsSna_Lu3270AssignedToPool Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 508c561d-6ee7-4813-863e-4faaa16fd6e9
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
