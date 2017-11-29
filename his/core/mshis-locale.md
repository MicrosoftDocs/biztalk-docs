---
title: "MsHis_Locale2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0be47e9c-e709-492d-92ae-369d6f80e949
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# MsHis_Locale
The **MsHIS_Locale** class is used to query for locale support.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsHis_Locale : MsHis_Config  
{  
   uint32 ID;  
   string Name;  
   boolean Available;  
};  
```  
  
## Properties  
 **ID**  
 Data Type: **uint32**  
  
 Qualifiers: **Key**  
  
 Access Type: Read-Only  
  
 The locale identifier. Used for internal reference.  
  
 **Name**  
 Data Type: **String**  
  
 Access Type: Read-Only  
  
 The locale name.  
  
 **Available**  
 Data Type: **Boolean**  
  
 Access Type: Read-Only  
  
 **true** if the locale is available on the system; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [wmiHIS WMI Provider Classes](../core/wmihis-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)