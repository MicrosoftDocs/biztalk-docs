---
description: "Learn more about: MsHis_Locale"
title: "MsHis_Locale2"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
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
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [wmiHIS WMI Provider Classes](../core/wmihis-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
