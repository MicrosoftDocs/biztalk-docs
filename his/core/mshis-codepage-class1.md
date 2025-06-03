---
description: "Learn more about: MsHis_CodePage Class"
title: "MsHis_CodePage Class1"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
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
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [wmiHIS WMI Provider Classes](../core/wmihis-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
