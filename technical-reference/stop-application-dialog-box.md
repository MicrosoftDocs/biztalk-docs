---
description: "Learn more about: Stop Application Dialog Box"
title: Stop Application Dialog Box
TOCTitle: Stop Application Dialog Box
ms:assetid: 2941db8a-24c6-4ebf-bf45-03827e9d9491
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559315(v=BTS.80)
ms:contentKeyID: 51526970
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.application.stop.dialog
---

# Stop Application Dialog Box

Use the **Stop Application** dialog box to suspend all activation messages, unenlist orchestrations and send ports, disable receive locations, and control running artifact instances.

The following table describes the UIElements in the collapsed form of the **Stop Application** dialog box.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Stop</strong></td>
<td>Click to stop the application and execute selected tasks.</td>
</tr>
<tr class="even">
<td><strong>Options</strong></td>
<td>Click to expand the <strong>Stop Application</strong> dialog box or, if the dialog box is already expanded, to collapse it.</td>
</tr>
</tbody>
</table>


## Options Tab

The following table describes the UIElements in the **Options** tab.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Partial Stop - Allow running instances to continue</strong></td>
<td>Select to disable only receive locations. Receive locations will stop receiving inbound messages and submitting them to the Message Box.</td>
</tr>
<tr class="even">
<td><strong>Partial Stop - Suspend running instances</strong></td>
<td>Select to disable receive locations and to stop all orchestrations and send ports. Receive locations will stop receiving inbound messages and submitting them to the Message Box. Orchestration subscriptions will be disabled, and send port subscriptions will be removed.</td>
</tr>
<tr class="odd">
<td><strong>Full Stop - Terminate instances</strong></td>
<td>Select to disable receive locations, unenlist orchestrations and send ports, and undeploy policies. Receive locations will stop receiving inbound messages and submitting them to the Message Box. Orchestration subscriptions will be disabled, and send port subscriptions will be removed. All policies (rules) will be removed from production.</td>
</tr>
</tbody>
</table>

## Referenced Applications Tab

Each check box represents an application that is referenced by the current one. If the check box next to an application name is selected, that application will stop when the current application stops.

The following table describes the UIElements in the **Referenced Applications** tab.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>&lt;application name&gt; Application</strong></td>
<td>Select the check box for each referenced application that you want to include when you stop the application.</td>
</tr>
</tbody>
</table>

## See Also

[Undeploying BizTalk Applications](https://msdn.microsoft.com/library/aa559800\(v=bts.80\))  
[How to Delete a BizTalk Application from the BizTalk Group](https://msdn.microsoft.com/library/aa577446\(v=bts.80\))
