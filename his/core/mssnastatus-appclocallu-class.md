---
title: "MsSnaStatus_AppcLocalLu Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9fa1f154-639b-433f-87bd-5178672d3aa4
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# MsSnaStatus_AppcLocalLu Class
The **MsSnaStatus_AppcLocalLu** class represents an APPC Local LU status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_AppcLocalLu : MsSnaStatus_Config  
{  
   string Name;  
   string ServiceName;  
   uint16 SessionLimit;  
   uint16 SessionCount;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The Local LU alias.  
  
 **ServiceName**  
 Data Type: **String** Access Type: Read-Only  
  
 The name of the SNA service on which this Local LU is defined.  
  
 **SessionLimit**  
 Data Type: **uint16** Access Type: Read-Only  
  
 The session limit for the LU.  
  
 **SessionCount**  
 Data Type: **uint16** Access Type: Read-Only  
  
 The current session count.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
  
 For more information on **GetObject** and **EnumerateInstances**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)