---
title: "MsSna_AppcPartner Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 32fdd1a1-1882-4702-b359-918cbbd9503b
caps.latest.revision: 4
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)