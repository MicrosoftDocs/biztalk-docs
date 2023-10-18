---
description: "Learn more about: MsSna_AccountAvailableAppcLu Class"
title: "MsSna_AccountAvailableAppcLu Class1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
