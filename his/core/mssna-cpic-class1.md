---
title: "MsSna_Cpic Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c93129ac-b4ca-413e-a612-52a2cc4caaa0
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_Cpic Class
A global CPI-C definition for APPC.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_Cpic : MsSna_Config  
{  
   String Name;  
   String ApplicationTPName;  
   String ServiceTPHexName;  
   String FullLUName;  
   String FullNetName;  
   sint16 SecurityType;  
   String UserId;  
   String Password;  
   String AliasLUName;  
   sint16 LUNameType;  
   sint16 TPNameType;  
   String ModeName;  
};  
```  
  
#### Parameters  
 **Name**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(8), TOUPPERCASE** Access Type: Read-Only  
  
 The Symbolic Destination name.  
  
 **Comment**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(25)</strong>Access Type: Read/Write  
  
 An optional comment field.  
  
 **ApplicationTPName**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(64)</strong>Access Type: Read/Write  
  
 The application TP name.  
  
 **ServiceTPHexName**  
 Data Type: **String** Qualifiers: **MAXLEN(8)** Access Type: Read/Write  
  
 A hexadecimal value describing the SNA service TP number.  
  
 **FullLUName**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE**Access Type: Read/Write  
  
 The partner LU name. Valid only for identifying a partner LU with a fully qualified name.  
  
 **FullNetName**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(8)</strong>Access Type: Read/Write  
  
 The partner network name. Valid only for identifying a partner LU with a fully qualified name.  
  
 **SecurityType**  
 Data Type: **sint16** Qualifiers: **QualiferValueHere** Access Type: Read/Write  
  
 The **Conversation Security** option to be used. The following table describes the possible values for **SecurityType**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|None|  
|1|Same|  
|2|Program|  
  
 **UserId**  
 Data Type: **String** Qualifiers: **MAXLEN(10)** Access Type: Read/Write  
  
 The user ID to be used when specifying *Program* for **SecurityType**.  
  
 **Password**  
 Data Type: **String** Qualifiers: **MAXLEN(10)** Access Type: Read/Write  
  
 The password to be used when specifying *Program* for **SecurityType**  
  
 **AliasLUName**  
 Data Type: **String** Qualifiers: MAXLEN(8), TOUPPERCASE Access Type: Read/Write  
  
 An alias. Valid only when identifying the Partner LU by alias.  
  
 **LUNameType**  
 Data Type: **sint16** Access Type: Read/Write  
  
 A value that indicates whether the Partner LU name is specified with an alias or a fully qualified LU name. The following table describes the possible values for **LUNameType**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Alias|  
|1|Full|  
  
 **TPNameType**  
 Data Type: **sint16** Qualifiers: **QualiferValueHere** Access Type: Read/Write  
  
 A value that indicates whether the Partner TP name is specified in characters or hex. The following table describes the possible values for **TPNameType**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Character|  
|1|Hex|  
  
 **ModeName**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE**Access Type: Read/Write  
  
 The name of the mode to be used.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)