---
title: "MsSna_Pool Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c721c108-8da3-4998-94a4-cf7fb4b9ddae
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# MsSna_Pool Class
Base class for 3270 LU pools.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_Pool : MsSna_Resource  
{  
   String Name;  
   String Comment;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**Qualifiers: **Key, MAXLEN(8)**Access Type: Read-Only  
  
 The pool name.  
  
 **Comment**  
 Data Type: **String**Qualifiers: **MAXLEN(25)**Access Type: Read/Write  
  
 An optional comment field.  
  
## Remarks  
 A pool is associated with one or more 3270 LUs.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)