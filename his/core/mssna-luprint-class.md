---
title: "MsSna_LuPrint Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec742011-8765-490a-871d-2fd1a35d888d
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)