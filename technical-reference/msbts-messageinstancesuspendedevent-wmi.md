---
description: "Learn more about: MSBTS_MessageInstanceSuspendedEvent (WMI)"
title: MSBTS_MessageInstanceSuspendedEvent (WMI)
TOCTitle: MSBTS_MessageInstanceSuspendedEvent (WMI)
ms:assetid: 9ec47256-6056-4564-9f77-bbea2c111083
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577626(v=BTS.80)
ms:contentKeyID: 51530074
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_MessageInstanceSuspendedEvent (WMI)

 

Represents a suspended event for a BizTalk Message Queuing (MSMQT) message instance.

## Declaration

```C#
class MSBTS_MessageInstanceSuspendedEvent : _ExtrinsicEvent  
```

## Members

**MSBTS\_MessageInstanceSuspendedEvent** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-messageinstancesuspendedevent-errorcategory-property-wmi.md">ErrorCategory</a></td>
<td>Contains the error category when the service instance is suspended.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstancesuspendedevent-errordescription-property-wmi.md">ErrorDescription</a></td>
<td>Contains the error description when the service instance is suspended.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstancesuspendedevent-errorid-property-wmi.md">ErrorId</a></td>
<td>Contains the error code when the service instance is suspended.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstancesuspendedevent-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the BizTalk Host that corresponds to this queue.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstancesuspendedevent-messageinstanceid-property-wmi.md">MessageInstanceID</a></td>
<td>Contains the ID of this message.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstancesuspendedevent-messagetype-property-wmi.md">MessageType</a></td>
<td>This property is not supported in the current release. This information can be retrieved by using the <a href="msbts-messageinstance-context-property-wmi.md">Context</a> property of the <strong>MSBTS_MessageInstance</strong> class.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstancesuspendedevent-referencetype-property-wmi.md">ReferenceType</a></td>
<td>Contains information about how this message is referenced by a service.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstancesuspendedevent-serviceclass-property-wmi.md">ServiceClass</a></td>
<td>Contains the class of the service instance to which this message belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstancesuspendedevent-serviceclassid-property-wmi.md">ServiceClassID</a></td>
<td>Contains the GUID of the service class that the service instance referencing this message belongs to.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstancesuspendedevent-serviceinstanceid-property-wmi.md">ServiceInstanceID</a></td>
<td>Contains the ID of the service instance in which this message belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstancesuspendedevent-servicetypeid-property-wmi.md">ServiceTypeID</a></td>
<td>Contains the GUID of the service type that the service instance referencing this message belongs to.</td>
</tr>
</tbody>
</table>


## Remarks

If BizTalk Server has fired an event, the server fails, and the suspend action was not committed due to the server failure; the Messaging Engine will try to suspend the instance again causing the event to fire again upon server start up.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

