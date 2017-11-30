---
title: "MsHis_CodePage Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72032fa0-c1ec-4d9f-8074-850d63201e74
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MsHis_CodePage Class
The **MsHIS_CodePage** class is used to query for code page support.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsHis_CodePage : MsHis_Config  
{  
   uint32 ID;  
   string Name;  
   boolean Available;  
   uint32 CodePage;  
   boolean DBCSEnabled;  
   boolean SBCSEnabled;  
   boolean MBCSEnabled;  
   boolean EuroEnabled;  
};  
```  
  
## Properties  
 **ID**  
 Data Type: **uint32**  
  
 Qualifiers: **Key**  
  
 Access Type: Read-Only  
  
 The code page identifier. Used for internal reference.  
  
 **Name**  
 Data Type: **String**  
  
 Access Type: Read-Only  
  
 The name of the code page.  
  
 **Available**  
 Data Type: **Boolean**  
  
 Access Type: Read-Only  
  
 **true** if the code page is supported by code page translations using SNANLS; otherwise, **false**.  
  
 **CodePage**  
 Data Type: **uint32**  
  
 Access Type: Read-Only  
  
 The number of the NLS code page.  
  
 **DBCSEnabled**  
 Data Type: **Boolean**  
  
 Access Type: Read-Only  
  
 **true** if this code page supports Double Byte Character Sets; otherwise, **false**.  
  
 **SBCSEnabled**  
 Data Type: **Boolean**  
  
 Access Type: Read-Only  
  
 **true** if this code page supports Single Byte Character Sets; otherwise, **false**.  
  
 **MBCSEnabled**  
 Data Type: **Boolean**  
  
 Access Type: Read-Only  
  
 **true** if this code page supports Multi-Byte Character Sets; otherwise, **false**.  
  
 **EuroEnabled**  
 Data Type: **Boolean**  
  
 Access Type: Read-Only  
  
 **true** if this code page has Euro support; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [wmiHIS WMI Provider Classes](../core/wmihis-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)