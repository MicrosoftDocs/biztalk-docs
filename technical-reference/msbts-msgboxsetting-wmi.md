---
description: "Learn more about: MSBTS_MsgBoxSetting (WMI)"
title: MSBTS_MsgBoxSetting (WMI)
TOCTitle: MSBTS_MsgBoxSetting (WMI)
ms:assetid: f4e245bf-a643-4367-a165-fb34872fa19a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561943(v=BTS.80)
ms:contentKeyID: 51533423
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MsgBoxSetting (WMI)

 

Represents a single MessageBox setting in the Microsoft BizTalk Server group.

## Declaration

```C#
class MSBTS_MsgBoxSetting : MSBTS_Setting  
```

## Members

**MSBTS\_MsgBoxSetting** defines the following properties:

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
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20246">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20246">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-msgboxsetting-disablenewmessagepublication-property-wmi.md">DisableNewMessagePublication</a></td>
<td>Enables or disables the publication of new messages in the MessageBox setting.</td>
</tr>
<tr class="even">
<td><a href="msbts-msgboxsetting-ismastermsgbox-property-wmi.md">IsMasterMsgBox</a></td>
<td>Indicates whether this MessageBox is the master MessageBox.</td>
</tr>
<tr class="odd">
<td><a href="msbts-msgboxsetting-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connection string. <strong>Note:</strong> The BizTalk Management database is also referred to as the BizTalk Configuration database.</td>
</tr>
<tr class="even">
<td><a href="msbts-msgboxsetting-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-msgboxsetting-msgboxdbname-property-wmi.md">MsgBoxDBName</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-msgboxsetting-msgboxdbservername-property-wmi.md">MsgBoxDBServerName</a></td>
<td>Contains the name of the SQL Server where the MessageBox setting database is located.</td>
</tr>
<tr class="odd">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20246">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
</tbody>
</table>


**MSBTS\_MsgBoxSetting** defines the following method:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-msgboxsetting-forcedelete-method-wmi.md">ForceDelete</a></td>
<td>Deletes the MessageBox object.</td>
</tr>
</tbody>
</table>


## Remarks

For more information about the minimum security user rights required to administer the MessageBox database, see [Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\)).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
