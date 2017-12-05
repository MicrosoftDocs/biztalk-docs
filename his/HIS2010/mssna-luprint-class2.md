---
title: "MsSna_LuPrint Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44be5092-0a23-41ee-be3f-d4b1a5cad7f6
caps.latest.revision: 4
---
# MsSna_LuPrint Class
Describes a 3270 LU printer resource.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuPrint   : MsSna_Lu3270  
{  
   String AssociatedLU;  
};  
```  
  
## Properties  
 **AssociatedLU**  
 Data Type: **String**Qualifiers: **MAXLEN(8)**Access Type: Read/Write  
  
 The associated display LU.  
  
## Remarks  
 **MsSna_LuPrint** is used by Print session or by printer emulation.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../HIS2010/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)