---
title: "MsSna_LuPassThrough Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 401b7595-4906-41bb-baa7-a80366188773
caps.latest.revision: 4
---
# MsSna_LuPassThrough Class
Contains one half of a dowstream LU/pool pair.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuPassThrough : MsSna_Config  
{  
   String Connection;  
   sint16 Number;  
   String Name;  
   boolean IsPool;  
};  
```  
  
## Properties  
 **Connection**  
 Data Type: **String**Qualifiers: **Key, MAXLEN(8)**Access Type: Read-Only  
  
 The associated downstream connection.  
  
 **Number**  
 Data Type: **sint16**Qualifiers: **Key, MINVALUE(0)**Access Type: Read-Only  
  
 The number of the downstream connection.  
  
 **Name**  
 Data Type: **String**Qualifiers: **MAXLEN(8)**Access Type: Read/Write  
  
 The downstream LU or pool name.  
  
 **IsPool**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to indicate that the object is a downstream a pool; **false** to indicate that the object is a downstream LU.  
  
## Remarks  
 **MsSna_LuPassThrough** represents a downstream LU/pool associated with a downstream connection.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../HIS2010/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)