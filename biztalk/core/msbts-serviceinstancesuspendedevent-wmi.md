---
title: "MSBTS_ServiceInstanceSuspendedEvent (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d07e5f2-0dae-4128-8f67-ade1a59d3fe4
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServiceInstanceSuspendedEvent (WMI)
Represents a suspended event for a service instance.  
  
## Syntax  
  
```  
  
class MSBTS_ServiceInstanceSuspendedEvent : _ExtrinsicEvent  
```  
  
## Members  
 **MSBTS_ServiceInstanceSuspendedEvent** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[ErrorCategory](../core/msbts-serviceinstancesuspendedevent-errorcategory-property-wmi.md)|Contains the error category when the service instance is suspended.|  
|[ErrorDescription](../core/msbts-serviceinstancesuspendedevent-errordescription-property-wmi.md)|Contains the error description when the service instance is suspended.|  
|[ErrorId](../core/msbts-serviceinstancesuspendedevent-errorid-property-wmi.md)|Contains the error code when the service instance is suspended.|  
|[HostName](../core/msbts-serviceinstancesuspendedevent-hostname-property-wmi.md)|Contains the name of the BizTalk Host that corresponds to this queue.|  
|[InstanceID](../core/msbts-serviceinstancesuspendedevent-instanceid-property-wmi.md)|Contains the ID of the service instance to which this message belongs.|  
|[ServiceClass](../core/msbts-serviceinstancesuspendedevent-serviceclass-property-wmi.md)|Contains the class of the service instance to which this message belongs.|  
|[ServiceClassID](../core/msbts-serviceinstancesuspendedevent-serviceclassid-property-wmi.md)|Contains the GUID of the service class that the service instance referencing this message belongs to.|  
|[ServiceStatus](../core/msbts-serviceinstancesuspendedevent-servicestatus-property-wmi.md)|Contains the state of the service instance.|  
|[ServiceTypeID](../core/msbts-serviceinstancesuspendedevent-servicetypeid-property-wmi.md)|Contains the GUID of the service type that the service instance referencing this message belongs to.|  
  
## Remarks  
 For sample code illustrating the **MSBTS_ServiceInstanceSuspendedEvent** class, see [Listening for a Suspended Event Using WMI](../core/listening-for-a-suspended-event-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.