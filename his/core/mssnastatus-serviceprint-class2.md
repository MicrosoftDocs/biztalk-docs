---
title: "MsSnaStatus_ServicePrint Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 086a2b9a-f113-49c4-b3c3-1ffa38eca502
caps.latest.revision: 4
---
# MsSnaStatus_ServicePrint Class
The **MsSnaStatus_ServicePrint** class represents an SNA Print service status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_ServicePrint : MsSnaStatus_Config  
{  
   string Name;  
   sint32 Status;  
   string StatusText;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The name of the Print Service. **Name** will be the same as the computer name.  
  
 **Status**  
 Data Type: **sint32** Access Type: Read-Only  
  
 The current status of the service. The following table describes the possible values for **Status**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Inactive|  
|1|Pending|  
|2|Stopping|  
|3|Active|  
  
 **StatusText**  
 Data Type: **String** Access Type: Read-Only  
  
 One of the **Status** values.  
  
 **Mode**  
 Data Type: **String** Access Type: Read-Only  
  
 The mode name for this session.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
|ExecMethod|Executes the specified method.|  
|[Start](../core/mssnastatus-serviceprint-start-method2.md)|Starts the print service.|  
|[Stop](../core/mssnastatus-serviceprint-stop-method1.md)|Stops the print service|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)