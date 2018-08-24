---
title: Application Properties Dialog Box
TOCTitle: Application Properties Dialog Box
ms:assetid: 3b6b33e4-079c-4114-a152-cde2f9ae1cbc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559675(v=BTS.80)
ms:contentKeyID: 51527404
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.application.properties
---

# Application Properties Dialog Box

 

Use the **Application Properties** window to set one application as the default and to reference other applications.

## General Tab

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Name</strong></td>
<td>Type the application display name. The name must be unique.</td>
</tr>
<tr class="even">
<td><strong>Make this the default application</strong></td>
<td>Select this check box to set the selected application as the default application. Artifacts (such as orchestrations, ports, maps, and schemas) that were deployed without an application specified are associated with the default application. If the check box is selected and unavailable, then the current application is already the default. To make another application the default, open the <strong>Application Properties</strong> window for that application and select the <strong>Make this the default application</strong> check box.</td>
</tr>
<tr class="odd">
<td><strong>Description</strong></td>
<td>Type any text that will help you distinguish this application from others. The maximum number of characters allowed is 1024.</td>
</tr>
</tbody>
</table>


## References Tab

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>This application refers to the following applications</strong></td>
<td>Displays a list of application references that have been added to this application. You add application references in the <strong>Add Application References</strong> dialog box.</td>
</tr>
<tr class="even">
<td><strong>Add</strong></td>
<td>Click to add a new application reference to the current application.</td>
</tr>
<tr class="odd">
<td><strong>Remove</strong></td>
<td>Click to remove the selected application reference.</td>
</tr>
<tr class="even">
<td><strong>The following applications depend on this application</strong></td>
<td>Displays a list of applications that reference the current application.</td>
</tr>
</tbody>
</table>


## See Also

[How to Install a BizTalk Application](https://msdn.microsoft.com/en-us/library/aa577503\(v=bts.80\))  
[Understanding BizTalk Application Deployment and Management](https://msdn.microsoft.com/en-us/library/aa560022\(v=bts.80\))  
[Importing BizTalk Applications, Bindings, and Policies](https://msdn.microsoft.com/en-us/library/aa560565\(v=bts.80\))  
[How to Import a BizTalk Application](https://msdn.microsoft.com/en-us/library/aa560132\(v=bts.80\))  
[How to Export a BizTalk Application](https://msdn.microsoft.com/en-us/library/aa577804\(v=bts.80\))

