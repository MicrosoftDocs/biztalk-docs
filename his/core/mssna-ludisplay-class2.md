---
title: "MsSna_LuDisplay Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55794ef5-94b0-4b63-b918-9984920bcbd3
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_LuDisplay Class
Describes a 3270 LU display resource.  
  
## Syntax  
  
```  
  
class MsSna_LuDisplay : MsSna_Lu3270  
{  
   sint16 Model;  
   boolean ModelOverride;  
   String AssociatedLU;  
};  
```  
  
## Properties  
 **Model**  
 Data Type: **sint16**Access Type: Read/Write  
  
 The default display model for Terminal service. The following table describes the possible values for **Model**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Model12|  
|1|Model13|  
|2|Model14|  
|3|Model1215|  
  
 **ModelOverride**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to indicate whether the default model can be overridden; otherwise, **false**. Some emulators can only emulate certain display models.  
  
 **AssociatedLU**  
 Data Type: **String**Qualifiers:<strong>MAXLEN(8)</strong>Access Type: Read-Only  
  
 Associates a printer LU with the current object.  
  
## Remarks  
 **MsSna_LuDisplay** is often used for terminal emulator access.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)