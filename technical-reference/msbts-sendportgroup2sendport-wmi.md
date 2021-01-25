---
description: "Learn more about: MSBTS_SendPortGroup2SendPort (WMI)"
title: MSBTS_SendPortGroup2SendPort (WMI)
TOCTitle: MSBTS_SendPortGroup2SendPort (WMI)
ms:assetid: 9479d9be-7a24-4bed-a591-5ddf1e089b6a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577403(v=BTS.80)
ms:contentKeyID: 51529785
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPortGroup2SendPort (WMI)

 

Represents the many to many relations between the send ports and the send port groups defined by BizTalk server.

## Declaration

```C#
class MSBTS_SendPortGroup2SendPort : MSBTS_Setting  
```

## Members

**MSBTS\_SendPortGroup2** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Caption (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendportgroup2sendport-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendportgroup2sendport-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendportgroup2sendport-sendportgroupname-property-wmi.md">SendPortGroupName</a></td>
<td>Contains the name of the send port group.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendportgroup2sendport-sendportname-property-wmi.md">SendPortName</a></td>
<td>Contains the name of the send port.</td>
</tr>
<tr class="odd">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
</tbody>
</table>


## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

