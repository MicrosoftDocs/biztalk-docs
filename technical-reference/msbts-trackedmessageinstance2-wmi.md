---
title: MSBTS_TrackedMessageInstance2 (WMI)
TOCTitle: MSBTS_TrackedMessageInstance2 (WMI)
ms:assetid: 63780b56-6364-4483-92c3-144835c8a2eb
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560495(v=BTS.80)
ms:contentKeyID: 51528516
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_TrackedMessageInstance2 (WMI)

 

This class reflects tracked message instances stored in the MessageBox database or Archived database. This class only supports GetObject and does not support Create/Update/Delete/Enum operations.

## Declaration

class MSBTS\_TrackedMessageInstance2 : MSBTS\_BTSObject

## Members

<table>
<thead>
<tr class="header">
<th>Property name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-trackedmessageinstance2-messageinstanceid-property-wmi.md">MSBTS_TrackedMessageInstance2.MessageInstanceID Property (WMI)</a></td>
<td>This property contains the ID of this message.</td>
</tr>
<tr class="even">
<td><a href="msbts-trackedmessageinstance2-sourcedbservername-property-wmi.md">MSBTS_TrackedMessageInstance2.SourceDBServerName Property (WMI)</a></td>
<td>Name of the SQL server where the tracked message is stored.</td>
</tr>
<tr class="odd">
<td><a href="msbts-trackedmessageinstance2-sourcedbname-property-wmi.md">MSBTS_TrackedMessageInstance2.SourceDBName Property (WMI)</a></td>
<td>Name of the SQL database where the tracked message is stored.</td>
</tr>
<tr class="even">
<td><a href="msbts-trackedmessageinstance2-mgmtdbnameoverride-property-wmi.md">MSBTS_TrackedMessageInstance2.MgmtDbNameOverride Property (WMI)</a></td>
<td>This optional property can be used to override the initial catalog part of the BizTalk Messaging Management database connect string, and represents the database name.</td>
</tr>
<tr class="odd">
<td><a href="msbts-trackedmessageinstance2-mgmtdbserveroverride-property-wmi.md">MSBTS_TrackedMessageInstance2.MgmtDbServerOverride Property (WMI)</a></td>
<td>This optional property can be used to override the data source part of the BizTalk Messaging Management database connect string.</td>
</tr>
<tr class="even">
<td><a href="msbts-trackedmessageinstance2-partcount-property-wmi.md">MSBTS_TrackedMessageInstance2.PartCount Property (WMI)</a></td>
<td>Number of message parts</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th>Method name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-trackedmessageinstance2-savetofile-method-wmi.md">MSBTS_TrackedMessageInstance2.SaveToFile Method (WMI)</a></td>
<td>This method saves message context and parts into multiple output files.</td>
</tr>
</tbody>
</table>


## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

