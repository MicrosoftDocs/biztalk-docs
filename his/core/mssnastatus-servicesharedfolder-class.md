---
title: "MsSnaStatus_ServiceSharedFolder Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75afb27e-1838-465e-b851-81794a3597b0
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# MsSnaStatus_ServiceSharedFolder Class
The **MsSnaStatus_ServiceSharedFolder** class represents a TN3270 service status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_ServiceSharedFolder : MsSnaStatus_Config  
{  
   string Name;  
   sint32 Status;  
   string StatusText;  
}  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The name of the service. **Name** will be the same as the local computer name.  
  
 **Status**  
 Data Type: **sint32** Qualifiers: **Key** Access Type: Read-Only  
  
 The status of the service. The following table describes the potential values for **Status**.  
  
|Value|Description|  
|-----------|-----------------|  
|0||  
|1|Inactive|  
|2|Pending|  
|3|Stopping|  
|4|Active|  
  
 **StatusText**  
 Data Type: **String** Access Type: Read-Only  
  
 One of the status values.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates the instance.|  
|ExecMethod|Executes the specified method.|  
|[Start](../core/mssnastatus-servicesharedfolder-start-method.md)|Starts the service.|  
|[Stop](../core/mssnastatus-servicesharedfolder-stop-method.md)|Stops the service.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see "IWbemServices interface" in the MSDN Library at http://msdn.microsoft.com/library.  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)