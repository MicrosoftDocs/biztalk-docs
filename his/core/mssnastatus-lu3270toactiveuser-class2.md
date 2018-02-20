---
title: "MsSnaStatus_Lu3270ToActiveUser Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16643023-926a-4564-b98b-7750138ee211
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
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
  
 For more information on **GetObject** and **EnumerateInstances** see [IWbemServices interface](https://msdn.microsoft.com/library/gg196568(v=vs.85).aspx). 
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)