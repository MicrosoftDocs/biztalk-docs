---
title: "MsSnaStatus_Lu3270ToActiveUser Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6c3e7ed-f4a1-4dee-8b91-8bdd977514f8
caps.latest.revision: 4
---
# MsSnaStatus_Lu3270ToActiveUser Class
The **MsSnaStatus_Lu3270ToActiveUser** class represents an association between a User connection and a 3270 type LU.  
  
## Syntax  
  
```  
  
class MsSnaStatus_Lu3270ToActiveUser : MsSnaStatus_Association  
{  
   MsSnaStatus_Lu3270 ref PathToLU3270;  
   MsSnaStatus_ActiveUser ref PathToUser;  
};  
```  
  
## Properties  
 **PathToLU3270**  
 Data Type: **MsSnaStatus_Lu3270 ref** Qualifiers: **Key** Access Type: Read-Only  
  
 The path to the APPC session.  
  
 **PathToUser**  
 Data Type: **MsSnaStatus_ActiveUser ref** Qualifiers: **Key** Access Type: Read-Only  
  
 The path to the user.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
  
 For more information on **GetObject** and **EnumerateInstances** see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)