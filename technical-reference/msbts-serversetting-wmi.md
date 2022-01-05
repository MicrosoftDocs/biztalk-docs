---
description: "Learn more about: MSBTS_ServerSetting (WMI)"
title: MSBTS_ServerSetting (WMI)
TOCTitle: MSBTS_ServerSetting (WMI)
ms:assetid: 586cfcb0-3aff-429d-8b18-bad01c04c7ac
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560278(v=BTS.80)
ms:contentKeyID: 51528193
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerSetting (WMI)

 

Represents specific computers within the BizTalk group that have BizTalk Servers installed. Instances of this class are intended to be created and deleted internally through BizTalk Server only. Do not create or delete instance of this class explicitly through WMI.

## Declaration

```C#
class MSBTS_ServerSetting : MSBTS_Setting  
```

## Members

**MSBTS\_ServerSetting** defines the following properties:

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
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serversetting-name-property-wmi.md">Name</a></td>
<td>Contains the name of the server.</td>
</tr>
<tr class="even">
<td><a href="msbts-serversetting-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serversetting-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
</tbody>
</table>


## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.