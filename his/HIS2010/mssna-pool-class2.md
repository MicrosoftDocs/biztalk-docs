---
title: "MsSna_Pool Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e5c6527-8c95-4b29-a6c7-2594eb83cef0
caps.latest.revision: 4
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../HIS2010/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)