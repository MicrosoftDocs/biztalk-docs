---
title: "MsSna_AccountAvailableAppcLu Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23f73458-7bd4-4324-8b41-49f9d39522e1
caps.latest.revision: 4
---
# MsSna_AccountAvailableAppcLu Class
For the logged-on user account and workstation, the assigned APPC LU resources.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_AccountAvailableAppcLu : MsSna_Assigned  
{  
   String LocalLu;  
   String RemoteLu;  
   String Wks;  
   String IPAddress;  
   String MacAddress;  
};  
```  
  
## Properties  
 **LocalLu**  
 Data Type: **String** Qualifiers: **MAXLEN(8)** Access Type: Read/Write  
  
 The local LU name.  
  
 **RemoteLu**  
 Data Type: **String** Qualifiers: **MAXLEN(8)** Access Type: Read/Write  
  
 The remote LU name.  
  
 **Wks**  
 Data Type: **String** Qualifiers: **MAXLEN(20** Access Type: Read/Write  
  
 The workstation name.  
  
 **IPAddress**  
 Data Type: **String** Qualifiers: **MAXLEN(20)** Access Type: Read/Write  
  
 The workstation IP address.  
  
 **MacAddress**  
 Data Type: **String** Qualifiers: **MAXLEN(20)** Access Type: Read/Write  
  
 The MAC address.  
  
## Remarks  
 **MsSna_AccountAvailableAppcLu** is used in querying for the remote APPC LUs for a given local APPC LU on a given workstation and associated with the logged-on user.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../HIS2010/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)