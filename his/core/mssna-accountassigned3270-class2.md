---
title: "MsSna_AccountAssigned3270 Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 142523b7-d3ad-4ca6-9c3a-4270a89cfa0c
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_AccountAssigned3270 Class
This is used to query for 3270 LUs assigned to a specific workstation or user.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_AccountAssigned3270 : MsSna_Assigned  
{  
   String Wks;  
   String IPAddress;  
   String MacAddress;  
   String Account;  
   String Service;  
   String LU;  
   boolean IsPool;  
   boolean IsAssociatedPrinterLU;  
   boolean ModelOverridable;  
   sint16 Model;  
};  
```  
  
#### Parameters  
 **Wks**  
 Data Type: **String** Qualifiers<strong>: MAXLEN(20)</strong>Access Type: Read/Write  
  
 The workstation name. By default, returns LUs assigned to all workstations.  
  
 **IPAddress**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(20)</strong>Access Type: Read/Write  
  
 The workstation IP. By default, returns LUs assigned to all workstations.  
  
 **MacAddress**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(20)</strong>Access Type: Read/Write  
  
 A value that returns LUs configured to a specific media access control (MAC) address.  
  
 **Account**  
 Data Type: **String** Access Type: Read/Write  
  
 The user for which to query for LUs. By default, will return LUs assigned to all users.  
  
 **Service**  
 Data Type: **String** Access Type: Read/Write  
  
 The SNA service on which to query for LUs.  
  
 **LU**  
 Data Type: **String** Qualifiers: Key, MAXLEN(8) Access Type: Read/Write  
  
 A value that indicates whether the returned LU is part of an LU pool.  
  
 **IsPool**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that the returned LU is part of an LU pool; otherwise, **false**.  
  
 **IsAssociatedPrinterLU**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that the returned LU has an Associated Printer LU; otherwise, **false**.  
  
 **ModelOverridable**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that the returned LU has an display model which can be overridden; otherwise, **false**.  
  
 **Model**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The default display model of the returned LU. The following table describes the possible values for **Model**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Model12|  
|1|Model13|  
|2|Model14|  
|3|Model15|  
  
## Remarks  
 **MsSna_AccountAssigned3270** is used in querying for LUA LUs assigned to a workstation as well as to the specified user.  
  
 On specifying "" for **Workstation**, only the LUs for the user will be returned.  
  
 On specifying "\*" for **User**, the LUs for the logged in user will be returned.  
  
 If User is omitted, LUs assigned to all Users will be returned.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)