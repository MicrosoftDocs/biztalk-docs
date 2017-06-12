---
title: "MSBTS_MessageInstanceSuspendedEvent (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9ec47256-6056-4564-9f77-bbea2c111083
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MessageInstanceSuspendedEvent (WMI)
Represents a suspended event for a BizTalk Message Queuing (MSMQT) message instance.  
  
## Declaration  
  
```  
class MSBTS_MessageInstanceSuspendedEvent : _ExtrinsicEvent  
```  
  
## Members  
 **MSBTS_MessageInstanceSuspendedEvent** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[ErrorCategory](../core/msbts-messageinstancesuspendedevent-errorcategory-property-wmi.md)|Contains the error category when the service instance is suspended.|  
|[ErrorDescription](../core/msbts-messageinstancesuspendedevent-errordescription-property-wmi.md)|Contains the error description when the service instance is suspended.|  
|[ErrorId](../core/msbts-messageinstancesuspendedevent-errorid-property-wmi.md)|Contains the error code when the service instance is suspended.|  
|[HostName](../core/msbts-messageinstancesuspendedevent-hostname-property-wmi.md)|Contains the name of the BizTalk Host that corresponds to this queue.|  
|[MessageInstanceID](../core/msbts-messageinstancesuspendedevent-messageinstanceid-property-wmi.md)|Contains the ID of this message.|  
|[MessageType](../core/msbts-messageinstancesuspendedevent-messagetype-property-wmi.md)|This property is not supported in the current release. This information can be retrieved by using the [Context](../core/msbts-messageinstance-context-property-wmi.md) property of the **MSBTS_MessageInstance** class.|  
|[ReferenceType](../core/msbts-messageinstancesuspendedevent-referencetype-property-wmi.md)|Contains information about how this message is referenced by a service.|  
|[ServiceClass](../core/msbts-messageinstancesuspendedevent-serviceclass-property-wmi.md)|Contains the class of the service instance to which this message belongs.|  
|[ServiceClassID](../core/msbts-messageinstancesuspendedevent-serviceclassid-property-wmi.md)|Contains the GUID of the service class that the service instance referencing this message belongs to.|  
|[ServiceInstanceID](../core/msbts-messageinstancesuspendedevent-serviceinstanceid-property-wmi.md)|Contains the ID of the service instance in which this message belongs.|  
|[ServiceTypeID](../core/msbts-messageinstancesuspendedevent-servicetypeid-property-wmi.md)|Contains the GUID of the service type that the service instance referencing this message belongs to.|  
  
## Remarks  
 If BizTalk Server has fired an event, the server fails, and the suspend action was not committed due to the server failure; the Messaging Engine will try to suspend the instance again causing the event to fire again upon server start up.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.