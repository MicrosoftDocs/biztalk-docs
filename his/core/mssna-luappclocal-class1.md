---
title: "MsSna_LuAppcLocal Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b64091e9-d601-44a2-8b39-c0af7a958b9f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MsSna_LuAppcLocal Class
An APPC local LU resource.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuAppcLocal : MsSna_Config  
{  
   String Service;  
   String Alias;  
   String Comment;  
   String NetName;  
   String LUName;  
   boolean PoolMember;  
   String IncomingLu;  
   sint16 TpTimeout;  
   sint16 Number;  
   string Connection;  
   boolean SyncPoint;  
   String SyncPointClient;  
};  
```  
  
## Properties  
 **Service**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(20), TOUPPERCASE** Access Type: Read-Only  
  
 The SNA service to which this LU belongs.  
  
 **Alias**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(8), TOUPPERCASE** Access Type: Read-Only  
  
 The LU alias.  
  
 **Comment**  
 Data Type: **String** Qualifiers: **MAXLEN(25)** Access Type: Read/Write  
  
 An optional comment field.  
  
 **NetName**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The network name, which must match that configured on the remote computer.  
  
 **LUName**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The LU name, which can be the same as the LU alias.  
  
 **PoolMember**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that this LU is a member of the default outgoing Local APPC LU pool; otherwise, **false**.  
  
 **IncomingLu**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 An implicit incoming remote LU.  
  
 **TpTimeout**  
 Data Type: **sint16** Qualifiers: **MINVALUE(0), MAXVALUE(3600)** Access Type: Read/Write  
  
 The time-out value, in seconds. If you want to manually start the invokable TP, be sure to specify at least 60 seconds; this will give the operator sufficient time to perform the necessary actions.  
  
 **Number**  
 Data Type: **sint16** Qualifiers: **MINVALUE(0), MAXVALUE(254)** Access Type: Read/Write  
  
 The LU number, for dependent LUs.  
  
 **Connection**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The connection on which a dependent LU is configured.  
  
 **SyncPoint**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that you have a very specialized transaction program (TP) that requires Resync Service; otherwise, **false**.  
  
 **SyncPointClient**  
 Data Type: **String** Qualifiers: **MAXLEN(15)** Access Type: Read/Write  
  
 The IP address or the name of the client computer.  
  
## Remarks  
 **MsSna_LuAppcLocal** is used for LU 6.2 protocols.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)