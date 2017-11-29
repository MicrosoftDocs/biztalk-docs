---
title: "MsSnaStatus_EventTN3270Session Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f42f660-718a-4ced-84de-f073f3ef2917
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# MsSnaStatus_EventTN3270Session Class
The **MsSnaStatus_EventTN3270Session** class describes a change to the **EventTN3270Session** class.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSnaStatus_EventTN3270Session: MsSnaStatus_Event  
{  
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
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)