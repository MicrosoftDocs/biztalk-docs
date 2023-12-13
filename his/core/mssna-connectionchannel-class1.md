---
description: "Learn more about: MsSna_ConnectionChannel Class"
title: "MsSna_ConnectionChannel Class1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
