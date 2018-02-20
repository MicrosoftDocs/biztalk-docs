---
title: "MsSna_ConnectionChannel Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b020bea7-7a14-49ea-bb60-e8be7706bad1
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_ConnectionChannel Class
A type of SNA connection that uses channel links.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_ConnectionChannel : MsSna_Connection  
{  
   String Address;  
   String CtrlUnit;  
   sint32 MaxBtu;  
};  
```  
  
## Properties  
 **Address**  
 Data Type: **String** Qualifiers: **MAXLEN(2)** Access Type: Read/Write  
  
 A 2-digit hexadecimal number identifying the channel. The range is from 00 through FF; the default is FF.  
  
 **CtrlUnit**  
 Data Type: **String** Qualifiers: **MAXLEN(1)** Access Type: Read-Only  
  
 A value for the control unit image number. The range is 0 through F; the default is 0 (zero).  
  
 **MaxBtu**  
 Data Type: **String** Qualifiers: **MINVALUE(265), MAXVALUE(65536)** Access Type: Read/Write  
  
 The Maximum Basic Transmission Unit (BTU) length.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)