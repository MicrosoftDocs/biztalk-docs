---
title: "MsSnaStatus_EventServiceSna Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72b37bd8-ea8f-4e40-9a94-fbb28a8c898c
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSnaStatus_EventServiceSna Class
The **MsSnaStatus_EventServiceSna** class describes a change to the **EventServiceSna** class.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSnaStatus_EventServiceSna : MsSnaStatus_Event  
  
    object ref Path;  
    sint16 Action;  
};  
```  
  
## Remarks  
 **Path**  
 Data Type: **Object ref**Access Type: Read-Only  
  
 The relative path to the corresponding object.  
  
 **Action**  
 Data Type: **sint16** Access Type: Read-Only  
  
 The event that occurred to the object specified in **Path**. The following table describes the valid values for **Action**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Create|  
|1|Destroy|  
|2|Modify|  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)