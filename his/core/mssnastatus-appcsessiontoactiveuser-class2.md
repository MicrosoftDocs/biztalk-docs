---
title: "MsSnaStatus_APPCSessionToActiveUser Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63ff7014-7345-44ce-bdba-07a84d9aa04d
caps.latest.revision: 4
---
# MsSnaStatus_APPCSessionToActiveUser Class
The **MsSnaStatus_APPCSessionToActiveUser** class represents an association between a User connection and an APPC session.  
  
## Syntax  
  
```  
  
class MsSnaStatus_APPCSessionToActiveUser : MsSnaStatus_Association  
{  
   MsSnaStatus_AppcSession ref PathToAPPCSession;  
   MsSnaStatus_ActiveUser ref PathToUser;  
};  
```  
  
## Properties  
 **PathToAPPCSession**  
 Data Type: **MsSnaStatus_AppcSession ref** Qualifiers: **Key** Access Type: Read-Only  
  
 The path to the APPC session.  
  
 **PathToUser**  
 Data Type: **String**Qualifiers: **Key** Access Type: **MsSnaStatus_ActiveUser ref**  
  
 The path to the user.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
  
 For more information on **GetObject** and **EnumerateInstances**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)