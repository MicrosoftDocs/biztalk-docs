---
description: "Learn more about: MsSna_LinkService Class"
title: "MsSna_LinkService Class1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSna_LinkService Class
The abstract **MsSna_LinkService** class represents an SNA link service.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LinkService   
{  
   String Name;  
   String DllName;  
   Boolean IsRemotable;  
   String Title;  
   String DriverName;  
   uint32 Type;  
}  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key**, **MaxLen(8)** Access Type: Read-Only  
  
 A US_ASCII string containing the name of the link service. The name will be assigned automatically for a new link service.  
  
 **DllName**  
 Data Type: **String**Access Type: Read-Only  
  
 The name of the .dll that implements the link service.  
  
 **IsRemotable**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** if the link service can be used from a remote node; otherwise, **false**.  
  
 **Title**  
 Data Type: **String**Qualifiers: **MaxLen(255)** Access Type: Read/Write  
  
 The title of the link service, up to 128 symbols long.  
  
 **DriverName**  
 Data Type: **String** Access Type: Read-Only  
  
 The device driver associated with the link service.  
  
 **Type**  
 Data Type: **uint32** Access Type: Read-Only  
  
 The type of link service. The following table describes the possible values for **Type**.  
  
|Value|Meaning|  
|-----------|-------------|  
|3|SDLC|  
|4|X25|  
|10|DFT|  
|11|DLC8022|  
|31|TWINAX|  
|32|CHANNEL|  
|35|IPDLC|  
  
## Requirements  
 Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WmiSnaLinkServiceMS WMI Provider Classes](../core/wmisnalinkservicems-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
