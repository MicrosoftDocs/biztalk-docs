---
title: "MsSna_ConnectionX25 Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ba81891-e699-4497-af4b-03c31e08108f
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# MsSna_ConnectionX25 Class
Describes a type of SNA connection that uses X.25 protocol over dial-up or leased lines.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_ConnectionX25 : MsSna_Connection  
{  
   String Address;  
   sint16 PVCAlias;  
   sint16 VCType;  
   String X25Facility;  
   String X25UserData;  
   sint16 X25PacketSize;  
   sint16 X25WindowSize;  
   sint32 MaxBtu;  
};  
```  
  
#### Parameters  
 **Address**  
 Data Type: **String** Qualifiers: **MAXLEN(15), TOUPPERCASE** Access Type: Read/Write  
  
 The Switched Virtual Circuit (SVC) address of the host for connections using switched virtual circuit.  
  
 **PVCAlias**  
 Data Type: **sint16** Qualifiers: **MINVALUE(1), MAXVALUE(65535)** Access Type: Read/Write  
  
 The Permanent Virtual Circuit (PVC) alias of the host for connections using permanent virtual circuit.  
  
 **VCType**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The type of virtual circuit used by the connection. The following table describes the possible values for **VCType**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Switched|  
|1|Permanent|  
  
 **X25Facility**  
 Data Type: **String** Qualifiers: **MAXLEN(132), TOUPPERCASE** Access Type: Read/Write  
  
 The codes for any Facility Data required by your network provider or by the administrator of the remote system. Valid only for an SVC channel.  
  
 **X25UserData**  
 Data Type: **String** Qualifiers: **MAXLEN(32), TOUPPERCASE** Access Type: Read/Write  
  
 The codes for any User Data required by your network provider. Valid only for an SVC channel.  
  
 **X25PacketSize**  
 Data Type: **sint16** Qualifiers: **QualiferValueHere** Access Type: Read/Write  
  
 The maximum number of data bytes, not header bytes, to be sent in a frame. The following table describes the possible values for **X25PacketSize**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|64|  
|1|128|  
|2|256|  
|3|512|  
|4|1024|  
  
 **X23PacketSize** is valid only for a PVC channel.  
  
 **X25WindowSize**  
 Data Type: **sint16** Qualifiers: **MINVALUE(1), MAXVALUE(7)** Access Type: Read/Write  
  
 The maximum number of frames that the local system can send without receiving a response from the remote system. Valid only for a PVC channel.  
  
 **MaxBtu**  
 Data Type: **sin32** Qualifiers: **MINVALUE(265), MAXVALUE(16393)** Access Type: Read/Write  
  
 The Maximum Basic Transmission Unit (BTU) length.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)