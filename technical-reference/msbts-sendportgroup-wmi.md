---
title: MSBTS_SendPortGroup (WMI)
TOCTitle: MSBTS_SendPortGroup (WMI)
ms:assetid: 38ba51dd-d332-4300-9bc4-2eb1bbbc57a7
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559617(v=BTS.80)
ms:contentKeyID: 51527384
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPortGroup (WMI)

 

Represents group of send ports defined by the BizTalk Server.

## Declaration

```C#
class MSBTS_SendPortGroup : MSBTS_Setting  
```

## Members

**MSBTS\_SendPortGroup** defines the following properties:

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
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at http://go.microsoft.com/fwlink/p/?LinkID=20246.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at http://go.microsoft.com/fwlink/p/?LinkID=20246.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendportgroup-filter-property-wmi.md">Filter</a></td>
<td>Contains textual representation of the filter.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendportgroup-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendportgroup-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendportgroup-name-property-wmi.md">Name</a></td>
<td>Contains the name of the send port group.</td>
</tr>
<tr class="odd">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at http://go.microsoft.com/fwlink/p/?LinkID=20246.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendportgroup-status-property-wmi.md">Status</a></td>
<td>Displays the current status of the port.</td>
</tr>
</tbody>
</table>


**MSBTS\_SendPortGroup** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-sendportgroup-enlist-method-wmi.md">Enlist</a></td>
<td>Enlists the send port group.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendportgroup-start-method-wmi.md">Start</a></td>
<td>Starts the send port group.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendportgroup-stop-method-wmi.md">Stop</a></td>
<td>Stops the send port group.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendportgroup-unenlist-method-wmi.md">UnEnlist</a></td>
<td>Unenlists the send port group.</td>
</tr>
</tbody>
</table>


## Remarks

The **MSBTS\_SendPortGroup** class operates differently than the user interface to add a send port group using BizTalk Explorer. In BizTalk Explorer, you cannot create a send port group that contains no send ports. Using the **MSBTS\_SendPortGroup** class, you must create an empty group first, and then use the MSBTS**\_SendPortGroup2SendPort** class to add send ports to the group.


> [!NOTE]
> <P>If you create a send port group that contains no send ports, BizTalk Explorer will raise an error when the group is clicked. To avoid this, ensure that any send port groups you create contain at least one port.</P>



This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPortGroup** class.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

