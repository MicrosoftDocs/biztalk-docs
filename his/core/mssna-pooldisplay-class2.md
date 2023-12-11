---
description: "Learn more about: MsSna_PoolDisplay Class"
title: "MsSna_PoolDisplay Class2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSna_PoolDisplay Class
Contains the 3270 LU Display pool.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_PoolDisplay : MsSna_Pool  
{  
   sint16 Model;  
   boolean ModelOverride;  
   boolean AssocPrint;  
};  
```  
  
## Properties  
 **Model**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The default display model for terminal emulation. The following table describes the possible values for **Model**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Model2|  
|1|Model3|  
|2|Model4|  
|3|Model5|  
  
 **ModelOverride**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that the default model can be overridden; otherwise, **false**. Some emulators can only emulate certain display models.  
  
 **AssocPrint**  
 Data Type: **Boolean** Qualifiers: **Something** Access Type: Read/Write  
  
 **true** to associate a printer LU with this display LU pool; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11 and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
