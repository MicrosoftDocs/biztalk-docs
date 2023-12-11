---
description: "Learn more about: MsSna_AppcPartner Class"
title: "MsSna_AppcPartner Class2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11 and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
