---
title: "MsSna_TN3270Session Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6fc63bc2-9be9-4350-9981-5af72820fddd
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_TN3270Session Class
Describes the part of the TN3270 session that specifies client configuration.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_TN3270Session : MsSna_Config  
{  
   String Name;  
   String ConnectionName;  
   String Comment;  
   String PoolName;  
   sint16 Number;  
   boolean Compression;  
   boolean UserWksSecure;  
   String Service;  
   sint32 TnType;  
   sint32 NumSessions;  
   sint32 TermTypes;  
   String AssociatedLu;  
   sint32 Port;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(8)</strong>Access Type: Read-Only  
  
 The LU name.  
  
 **ConnectionName**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(8)</strong>Access Type: Read-Only  
  
 The connection on which this LU is defined.  
  
 **Comment**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(25)</strong>Access Type: Read/Write  
  
 An optional comment field.  
  
 **PoolName**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(8)</strong>Access Type: Read-Only  
  
 If the LU has already been assigned to a pool, the pool name appears here.  
  
 **Number**  
 Data Type: **sint16**Qualifiers: **MINVALUE(1), MAXVALUE(254)** Access Type: Read/Write  
  
 The LU Number for LUs on 802.2, SDLC, or X.25. For a DFT connection, this should be the Port Number * 16 + LT Number.  
  
 **Compression**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to enable 3270 LU data stream compression; otherwise, **false**. This option must also be set in the host VTAM configuration for the LU.  
  
 **UserWksSecure**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to require both the user and the workstation to be assigned to this LU in order to acquire it; otherwise, **false**.  
  
 **Service**  
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(20)</strong>Access Type: Read/Write  
  
 The SNA service to which this LU belongs.  
  
 **TnType**  
 Data Type: **sint32**Access Type: Read/Write  
  
 The display or printer type. The following table describes the possible values for **TnType**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Generic|  
|1|Specific|  
|2|GenericPrinter|  
|3|SpecificPrinter|  
|4|AssoicatedPrinter|  
  
 **NumSessions**  
 Data Type: **sint32**Qualifiers: <strong>MINVALUE(0), MAXVALUE(65535)</strong>Access Type: Read/Write  
  
 This is the number of TN3270 sessions allowed for the selected LU or pool.  
  
 **TermTypes**  
 Data Type: **sint32**Access Type: Read/Write  
  
 The terminal names supported by this LU. The following table describes the possible values for **TermTypes**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|3275-2|  
|1|3276_2|  
|2|3277_2|  
|3|3278_2|  
|4|3278_2_E|  
|5|3279_2|  
|6|3279_2_|  
|7|E 3276_3|  
|8|3278_3|  
|9|3278_3_E|  
|10|3279_3|  
|11|3279_3_E|  
|12|3276_4|  
|13|3278_4|  
|14|3278_4_E|  
|15|3279_4|  
|16|3279_4_E|  
|17|3278_5|  
|18|3278_5_E|  
|19|3279_5|  
|20|3279_5_E|  
  
 **AssociatedLu**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(8)</strong>Access Type: Read/Write  
  
 Used to associate a printer LU with this display LU.  
  
 **Port**  
 Data Type: **sint32**Qualifiers: <strong>MINVALUE(0), MAXVALUE(9999)</strong>Access Type: Read/Write  
  
 The port to be used for this session—or 0 to use the default TN3270 port.  
  
## Remarks  
 **MsSna_TN3270Session** references a SNA_LU_LUA class.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)