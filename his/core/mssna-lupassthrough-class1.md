---
title: "MsSna_LuPassThrough Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f956df5-cb1b-4562-8377-d2332a2fcb07
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)