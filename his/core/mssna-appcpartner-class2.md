---
title: "MsSna_AppcPartner Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1167c5c6-9540-430d-80f3-e9e367d12c8c
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MsSna_AppcPartner Class
A preconfigured combination of APPC local LU, remote LU, and Mode.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_AppcPartner : MsSna_Config  
{  
   String Mode;  
   String Server;  
   String LocalLUAlias;  
   String PartnerLUAlias;  
   String Connection;  
};  
```  
  
## Properties  
 **Mode**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The mode to be used in the partnership.  
  
 **Server**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(16), TOUPPERCASE** Access Type: Read/Write  
  
 The Host Integration Server name on which this partnership will be added.  
  
 **LocalLUAlias**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The Local LU alias to be used in the partnership.  
  
 **PartnerLUAlias**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The partner LU. **PartnerLUAlias** can be a Remote LU or a different Local LU.  
  
 **Connection**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The connection name for the Remote LU.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)