---
title: "MsSna_LuAppcRemote Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14c11b0e-fdce-4dc1-97e1-7834db2814ac
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MsSna_LuAppcRemote Class
An APPC remote LU resource.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuAppcRemote : MsSna_Config  
{  
   String Service;  
   String Connection;  
   String Alias;  
   String Comment;  
   String NetName;  
   String LUName;  
   String UnName;  
   boolean Parallel;  
   String IncomingMode;  
   sint16 Security;  
   String SecKeyHex;  
   String SecKeyChar;  
   boolean SyncPoint;  
};  
```  
  
## Properties  
 **Service**  
 Data Type: **String** Qualifiers: **MAXLEN(20), TOUPPERCASE** Access Type: Read-Only  
  
 The SNA service to which this LU belongs.  
  
 **Connection**  
 Data Type: **String** Qualifiers: **Key,MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The connection on which a dependent LU is configured.  
  
 **Alias**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(8)** Access Type: Read-Only  
  
 The LU Alias.  
  
 **Comment**  
 Data Type: **String** Qualifiers: **MAXLEN(25)** Access Type: Read/Write  
  
 An optional comment field.  
  
 **NetName**  
 Data Type: **String** Qualifiers: **MAXLEN(8)** Access Type: Read/Write  
  
 The network name. You can obtain the correct name from the host or peer administrator.  
  
 **LUName**  
 Data Type: **String** Qualifiers: **MAXLEN(8)** Access Type: Read/Write  
  
 The LU name, which can be the same as the LU alias.  
  
 **UnName**  
 Data Type: **String** Qualifiers: **MAXLEN(8)** Access Type: Read/Write  
  
 The uninterpreted LU name for LUs, which are paired with a dependent local APPC LU.  
  
 **Parallel**  
 Data Type: **String** Access Type: Read/Write  
  
 A value that indicates that parallel sessions will be used. **Parallel** must be used with an independent, local LU.  
  
 **IncomingMode**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The implicit incoming mode for this LU.  
  
 **Security**  
 Data Type: **sint16** Access Type: Read/Write  
  
 A value that indicates what sort of session-level security will be used with this LU. The following table describes the possible values for **Security**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|None|  
|1|Hex|  
|2|Characters|  
  
 **SecKeyHex**  
 Data Type: **String** Qualifiers: **MAXLEN(16)** Access Type: Read/Write  
  
 The security key, in hexadecimal. Requires that **Security** be set to '**1**'.  
  
 **SecKeyChar**  
 Data Type: **String** Qualifiers: **MAXLEN(8)** Access Type: Read/Write  
  
 The security key, in characters. Requires that **Security** be set to **2**.  
  
 **SyncPoint**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable **SyncPoint**; otherwise, **false**. **SyncPoint** requires that the Local LU alias be unique.  
  
## Remarks  
 **MsSna_LuAppcRemote** is used for LU 6.2 protocol, and references a connection.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)