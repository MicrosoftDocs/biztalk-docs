---
title: "MsSna_PoolDisplay Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 438af0fa-b087-4856-b146-8275b57be481
caps.latest.revision: 4
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)