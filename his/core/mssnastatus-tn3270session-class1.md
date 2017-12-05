---
title: "MsSnaStatus_TN3270Session Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3cf301bd-dbae-4b14-9079-881a42f7d0a1
caps.latest.revision: 4
---
# MsSnaStatus_TN3270Session Class
The **MsSnaStatus_TN3270Session** class represents a TN3270 session status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_TN3270Session : MsSnaStatus_Config  
{  
   string Name;  
   string Client;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The service name. **Name** will be identical to the LUA LU or Pool name.  
  
 **Client**  
 Data Type: **String** Access Type: Read-Only  
  
 The client computer name or IP address.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)