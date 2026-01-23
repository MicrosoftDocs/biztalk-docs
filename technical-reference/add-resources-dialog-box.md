---
description: "Learn more about: Add Resources Dialog Box"
title: Add Resources Dialog Box
TOCTitle: Add Resources Dialog Box
ms:assetid: c3e28cea-aeb2-4d93-a45e-faaa5a6d6533
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547874(v=BTS.80)
ms:contentKeyID: 51531139
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.resources.add
ms.topic: ui-reference
---

# Add Resources Dialog Box

Use the **Add Resources** dialog box to add assemblies, scripts, bindings, COM objects, and other resources to an application.

The following table describes the UIElements in the **Add Resources** dialog box.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Selected files to add - File Name</strong></td>
<td>Displays the name of the resource that you have selected to add to the application.</td>
</tr>
<tr class="even">
<td><strong>Selected files to add - Type</strong></td>
<td>Displays the type of resource that you have selected.</td>
</tr>
<tr class="odd">
<td><strong>Selected files to add - Source Location</strong></td>
<td>Displays the path to the location where the resource resides prior to being added to the application.</td>
</tr>
<tr class="even">
<td><strong>Add</strong></td>
<td>Displays the <strong>Select Files to Add</strong> dialog box, to which you can browse and select the resource to add to the application.</td>
</tr>
<tr class="odd">
<td><strong>Remove</strong></td>
<td>Click to remove the selected resource from the application.</td>
</tr>
<tr class="even">
<td><strong>Overwrite All</strong></td>
<td>Select this check box when you are adding a resource that you already know is in the database, but that you want to replace. If you do not select <strong>Overwrite All</strong>, an existing resource by the same name as one you are adding will cause the add process to fail.</td>
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
<td>Type the path of the location to which the resource file will be copied when the application is installed, including the resource file name. An absolute path, relative path, or Universal Naming Convention (UNC) path are all acceptable. Folders that do not exist will be created upon installation if required security rights are in place and there is sufficient space. The default value in this box is as follows: <em>path of application installation folder</em>\<em>resource file name</em>. The path of the installation folder is specified by the %BTAD_InstallDir% environment variable. Example: %BTAD_InstallDir%\MyResource.xml.</td>
</tr>
<tr class="even">
<td><strong>Options – Target Environment (BizTalkBinding File type)</strong></td>
<td>A string specifying which environment the binding file is associated with. If you choose this environment at import time, this binding file is applied. If you do not specify a string, this binding file is applied to all environments.</td>
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
