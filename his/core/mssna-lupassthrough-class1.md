---
description: "Learn more about: MsSna_LuPassThrough Class"
title: "MsSna_LuPassThrough Class1"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
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
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(8)</strong>Access Type: Read-Only  
  
 The associated downstream connection.  
  
 **Number**  
 Data Type: **sint16**Qualifiers: <strong>Key, MINVALUE(0)</strong>Access Type: Read-Only  
  
 The number of the downstream connection.  
  
 **Name**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(8)</strong>Access Type: Read/Write  
  
 The downstream LU or pool name.  
  
 **IsPool**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to indicate that the object is a downstream a pool; **false** to indicate that the object is a downstream LU.  
  
## Remarks  
 **MsSna_LuPassThrough** represents a downstream LU/pool associated with a downstream connection.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
