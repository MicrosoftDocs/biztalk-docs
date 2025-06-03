---
description: "Learn more about: MSBTS_SendHandler2 (WMI)"
title: MSBTS_SendHandler2 (WMI)
TOCTitle: MSBTS_SendHandler2 (WMI)
ms:assetid: 732a03ae-c699-45cc-be92-06cf9cac7ce1
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560809(v=BTS.80)
ms:contentKeyID: 51528923
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_SendHandler2 (WMI)

 

Represents an individual send handler defined by the BizTalk Server.

## Declaration

class MSBTS\_SendHandler2 : MSBTS\_Setting

## Members

<table>
<thead>
<tr class="header">
<th>Property Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-sendhandler2-adaptername-property-wmi.md">MSBTS_SendHandler2.AdapterName Property (WMI)</a></td>
<td>This property contains the name of the adapter used by the given instance.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendhandler2-customcfg-property-wmi.md">MSBTS_SendHandler2.CustomCfg Property (WMI)</a></td>
<td>This property contains adapter-specific configuration in XML format.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendhandler2-hostname-property-wmi.md">MSBTS_SendHandler2.HostName Property (WMI)</a></td>
<td>This property contains the name of the BizTalk Host for this transport handler.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendhandler2-hostnametoswitchto-property-wmi.md">MSBTS_SendHandler2.HostNameToSwitchTo Property (WMI)</a></td>
<td>This property contains the name of the BizTalk Host that this transport handler should switch to.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendhandler2-isdefault-property-wmi.md">MSBTS_SendHandler2.IsDefault Property (WMI)</a></td>
<td>This property indicates whether the send handler is the default one for this adapter type.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendhandler2-mgmtdbnameoverride-property-wmi.md">MSBTS_SendHandler2.MgmtDbNameOverride Property (WMI)</a></td>
<td>This optional property can be used to override the initial catalog part of the BizTalk Messaging Management database connect string, and represents the database name.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendhandler2-mgmtdbserveroverride-property-wmi.md">MSBTS_SendHandler2.MgmtDbServerOverride Property (WMI)</a></td>
<td>This optional property can be used to override the data source part of the BizTalk Messaging Management database connect string.</td>
</tr>
</tbody>
</table>


## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

