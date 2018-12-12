---
title: MSBTS_ServiceInstanceSuspendedEvent (WMI)
TOCTitle: MSBTS_ServiceInstanceSuspendedEvent (WMI)
ms:assetid: 0d07e5f2-0dae-4128-8f67-ade1a59d3fe4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547324(v=BTS.80)
ms:contentKeyID: 51526175
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServiceInstanceSuspendedEvent (WMI)

 

Represents a suspended event for a service instance.

## Syntax

```C#
  
class MSBTS_ServiceInstanceSuspendedEvent : _ExtrinsicEvent  
```

## Members

**MSBTS\_ServiceInstanceSuspendedEvent** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-serviceinstancesuspendedevent-errorcategory-property-wmi.md">ErrorCategory</a></td>
<td>Contains the error category when the service instance is suspended.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstancesuspendedevent-errordescription-property-wmi.md">ErrorDescription</a></td>
<td>Contains the error description when the service instance is suspended.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstancesuspendedevent-errorid-property-wmi.md">ErrorId</a></td>
<td>Contains the error code when the service instance is suspended.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstancesuspendedevent-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the BizTalk Host that corresponds to this queue.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstancesuspendedevent-instanceid-property-wmi.md">InstanceID</a></td>
<td>Contains the ID of the service instance to which this message belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstancesuspendedevent-serviceclass-property-wmi.md">ServiceClass</a></td>
<td>Contains the class of the service instance to which this message belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstancesuspendedevent-serviceclassid-property-wmi.md">ServiceClassID</a></td>
<td>Contains the GUID of the service class that the service instance referencing this message belongs to.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstancesuspendedevent-servicestatus-property-wmi.md">ServiceStatus</a></td>
<td>Contains the state of the service instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstancesuspendedevent-servicetypeid-property-wmi.md">ServiceTypeID</a></td>
<td>Contains the GUID of the service type that the service instance referencing this message belongs to.</td>
</tr>
</tbody>
</table>


## Remarks

For sample code illustrating the **MSBTS\_ServiceInstanceSuspendedEvent** class, see [Listening for a Suspended Event Using WMI](listening-for-a-suspended-event-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

