---
description: "Learn more about: Modify Resources Dialog Box"
title: Modify Resources Dialog Box
TOCTitle: Modify Resources Dialog Box
ms:assetid: 6974c4d6-55b1-479c-bdc0-fe1a917c1d36
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560604(v=BTS.80)
ms:contentKeyID: 51528670
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.resources.modify
---

# Modify Resources Dialog Box

Use the **Modify Resources** dialog box to modify options for assemblies, scripts, bindings, COM objects, and other resources and their properties that have been added to an application, or to replace these resources with updated versions bearing the same name.

The following table describes the UIElements in the **Modify Resources** dialog box.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Selected resources to modify - File Name</strong></td>
<td>Displays the name of the resource that has been added to the application.</td>
</tr>
<tr class="even">
<td><strong>Selected resources to modify - Type</strong></td>
<td>Displays the type of resource you have selected.</td>
</tr>
<tr class="odd">
<td><strong>Selected resources to modify - Source Location</strong></td>
<td>Displays the path to the location where the resource originally resided prior to being updated in the BizTalk application.</td>
</tr>
<tr class="even">
<td><strong>Refresh</strong></td>
<td>Click to replace the selected resource with an updated version of the resource by the same name. When you click <strong>Refresh</strong>, you replace the resource without deleting any option settings you may have made. The source location of the resource will change if you are updating the resource with a version taken from a different source location.</td>
</tr>
<tr class="odd">
<td><strong>Overwrite All</strong></td>
<td>This check box this unavailable because it is not possible to modify an existing resource without overwriting it.</td>
</tr>
</tbody>
</table>

## Options Tab

The **Options** tab displays special configuration for the resource you have selected in **Selected files to add**.

The following table lists the UIElements in the **Options** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Options - File type</strong></td>
<td>From the drop-down list, select the type of file you are adding as a resource. If you select <strong>Assembly</strong> or <strong>BizTalkAssembly</strong>, you must also specify any dependencies.</td>
</tr>
<tr class="even">
<td><strong>Options - Options</strong></td>
<td>Displays configuration options that you may select for the type of resource you have added. Not all resource types have options.</td>
</tr>
<tr class="odd">
<td><strong>Options - Destination location</strong></td>
<td>Type the path to the location where the resource will be stored and the filename. The default value in this box is the source location of the selected resource.</td>
</tr>
</tbody>
</table>

## Dependencies Tab

The **Dependencies** tab appears only when **Assembly** or **BizTalk Assembly** is selected in the **File type** list on the **Options** tab. It displays information about other files on which the selected resource has a dependency.

The following table lists the UIElements in the **Dependencies** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Dependent Assemblies - Name</strong></td>
<td>Displays the name, version, culture, and public key token of a resource upon which the assembly you have selected in <strong>Selected files to add</strong> depends.</td>
</tr>
<tr class="even">
<td><strong>Dependent Assemblies - Status</strong></td>
<td>Displays status information about the depended-upon assembly.</td>
</tr>
<tr class="odd">
<td><strong>Add to Application</strong></td>
<td>Click to select assembly files with which the new resource has a dependency.</td>
</tr>
</tbody>
</table>

## See Also

[Understanding BizTalk Application Deployment and Management](https://msdn.microsoft.com/library/aa560022\(v=bts.80\))
