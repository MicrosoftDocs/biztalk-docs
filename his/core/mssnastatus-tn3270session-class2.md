---
description: "Learn more about: MsSnaStatus_TN3270Session Class"
title: "MsSnaStatus_TN3270Session Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27d70a0a-5542-4a94-925a-0d6ffb5df438
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
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
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods). 
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)