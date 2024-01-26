---
description: "Learn more about: MsSnaStatus_AppcLocalLu Class"
title: "MsSnaStatus_AppcLocalLu Class2"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
  
 For more information on **GetObject** and **EnumerateInstances**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods).  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
