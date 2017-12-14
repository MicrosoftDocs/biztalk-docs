---
title: "MsSna_AppcMode Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6c10368-5687-4eac-960c-518cc2466a8d
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MsSna_AppcMode Class
Contains an APPC Mode definition.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_AppcMode : MsSna_Config  
{  
   String Name;  
   String Comment;  
   sint32 SessionLimit;  
   sint32 MinContWin;  
   sint32 PartMinContWin;  
   sint32 AutoActivate;  
   boolean Priority;  
   sint32 TxPacing;  
   sint32 RxPacing;  
   sint32 TxRu;  
   sint32 RxRu;  
   sint16 MaxSendCompression;  
   sint16 MaxRcvCompression;  
   boolean AllowLZandRLE;  
   boolean EndpointOnly;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read-Only  
  
 The mode name.  
  
 **Comment**  
 Data Type: **String** Qualifiers: **MAXLEN(25)** Access Type: Read/Write  
  
 An optional comment field.  
  
 **SessionLimit**  
 Data Type: **sint32** Qualifiers: **MINVALUE(0), MAXVALUE(15000)** Access Type: Read/Write  
  
 The maximum number of parallel sessions allowed with this mode.  
  
 **MinContWin**  
 Data Type: **sint32** Qualifiers: **MINVALUE(0), MAXVALUE(15000)** Access Type: Read/Write  
  
 The minimum contention winner limit.  
  
 **PartMinContWin**  
 Data Type: **sint32** Qualifiers: **MINVALUE(0), MAXVALUE(15000)** Access Type: Read/Write  
  
 The partner minimum contention winner limit.  
  
 **AutoActivate**  
 Data Type: **sint32** Qualifiers: **MINVALUE(0), MAXVALUE(15000)** Access Type: Read/Write  
  
 The number of contention winner sessions to be activated for the local LU whenever the connection for this mode is started.  
  
 **Priority**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to give preference to communication with this mode over communication with a low-priority mode; otherwise, **false**.  
  
 **TxPacing**  
 Data Type: **sint32** Qualifiers: **MINVALUE(0), MAXVALUE(63)** Access Type: Read/Write  
  
 The maximum number of frames for the local LU to send without an SNA pacing response from the partner LU. Setting **TxPacing** to 0 indicates a unlimited number of frames.  
  
 **RxPacing**  
 Data Type: **sint32** Qualifiers: **MINVALUE(0), MAXVALUE(63)** Access Type: Read/Write  
  
 The maximum number of frames for the local LU to receive from the partner LU before the local LU sends an SNA pacing response. Setting **RxPacing** to **0** (zero) indicates a unlimited number of frames.  
  
 **TxRu**  
 Data Type: **sint32** Qualifiers: **MINVALUE(256), MAXVALUE(65527)** Access Type: Read/Write  
  
 The maximum size for RUs sent by the TPs on the local system.  
  
 **RxRu**  
 Data Type: **sint32** Qualifiers: **MINVALUE(256), MAXVALUE(65527)** Access Type: Read/Write  
  
 The maximum size for RUs received from the TPs on the remote system.  
  
 **MaxSendCompression**  
 Data Type: **sint32** Access Type: Read/Write  
  
 The maximum compression allowed when sending. The following table describes the possible values for **MaxSendCompression**.  
  
|Values|Description|  
|------------|-----------------|  
|0|None|  
|1|RLE|  
|2|LZ9|  
  
 **MaxRcvCompression**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The maximum compression allowed when receiving. The following table describes the possible values for **MaxRcvCompression**.  
  
|Values|Description|  
|------------|-----------------|  
|0|None|  
|1|RLE|  
|2|LZ9|  
  
 **AllowLZandRLE**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to compress data using RLE before being further compressed using LZ9; otherwise, **false**. **AllowLZandRLE** is valid only if you are using LZ9.  
  
 **EndpointOnly**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to allow intermediate nodes to use compression if one of the endpoints does not support or otherwise does not use compression; otherwise, **false**.  
  
## Remarks  
 **MsSna_AppcMode** defines properties of an LU 6.2 session.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)