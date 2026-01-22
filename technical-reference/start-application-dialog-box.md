---
description: "Learn more about: Start Application Dialog Box"
title: Start Application Dialog Box
TOCTitle: Start Application Dialog Box
ms:assetid: 4276b81e-5d2e-4e59-a5a9-1401f61d9ce3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559804(v=BTS.80)
ms:contentKeyID: 51527577
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: ui-reference
f1_keywords:
- bts10.admin.application.start.dialog
---

# Start Application Dialog Box

Use the **Start Application** dialog box to start all dependent artifacts and applications in one transaction.

When you open this dialog box, it is displayed in a collapsed form (without the **Options** or **Referenced Applications** tab visible) if all applications that the current application references are already running. If any of the referenced applications have not already been started when you open this dialog box to start the current application, the dialog box will open with the **Details** portion of the dialog box expanded so that you can see the referenced applications that will also be started.

The following table describes the UIElements in the collapsed form of the **Start Application** dialog box.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Start</strong></td>
<td>Click to start the application and the selected artifacts and referenced applications.</td>
</tr>
<tr class="even">
<td><strong>Options</strong></td>
<td>Click to expand the <strong>Start Application</strong> dialog box and display the <strong>Options</strong> and <strong>Referenced Applications</strong> tabs.</td>
</tr>
</tbody>
</table>

## Options Tab

Each check box represents an application artifact that will start automatically when you start the application unless you specify otherwise. All check boxes are selected by default.

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
<td><strong>Application artifacts - Start all orchestrations</strong></td>
<td>Select this check box to start all orchestrations when you start the application.</td>
</tr>
<tr class="even">
<td><strong>Application artifacts - Start all send ports</strong></td>
<td>Select this check box to start all send ports when you start the application.</td>
</tr>
<tr class="odd">
<td><strong>Application artifacts - Start all send port groups</strong></td>
<td>Select this check box to include all send port groups when you start the application.</td>
</tr>
<tr class="even">
<td><strong>Application artifacts - Enable all receive locations</strong></td>
<td>Select this check box to enable receive locations when you start the application. Enabled receive locations can accept inbound messages and submit them to the Message Box.</td>
</tr>
<tr class="odd">
<td><strong>Application artifacts - Start all associated host instances</strong></td>
<td>Select this check box to enable host instances to begin processing documents when you start the application.</td>
</tr>
<tr class="even">
<td><strong>Deploy all policies</strong></td>
<td>Select this check box to deploy all policies (rules) when you start the application.</td>
</tr>
<tr class="odd">
<td><strong>Instances - Resume suspended instances</strong></td>
<td>Select this check box to resume suspended orchestration instances when you start the application.</td>
</tr>
</tbody>
</table>


## Referenced Applications Tab

Each check box represents an application that is referenced by the current one. If the check box next to an application name is selected, that application will start when the current application starts.

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
<td>Select the check box for each referenced application that you want to include when you start the application.</td>
</tr>
</tbody>
</table>

## See Also

[How to Import a BizTalk Application](https://msdn.microsoft.com/library/aa560132\(v=bts.80\))  
[How to Delete a BizTalk Application from the BizTalk Group](https://msdn.microsoft.com/library/aa577446\(v=bts.80\))  
[Deploying and Managing BizTalk Applications](https://msdn.microsoft.com/library/aa578693\(v=bts.80\))
