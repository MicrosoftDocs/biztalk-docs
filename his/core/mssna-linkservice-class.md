---
title: "MsSna_LinkService Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 625a4203-5505-45d5-81d1-f35350bfc0dc
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
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
 Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaLinkServiceMS WMI Provider Classes](../core/wmisnalinkservicems-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)