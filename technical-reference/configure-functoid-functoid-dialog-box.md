---
description: "Learn more about: Configure <Functoid> Functoid Dialog Box"
title: Configure <Functoid> Functoid Dialog Box
TOCTitle: Configure <Functoid> Functoid Dialog Box
ms:assetid: 1fd1d80f-c5c2-4ae7-8f29-c510c2927ef4
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559136(v=BTS.80)
ms:contentKeyID: 51526677
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.mapper.functoid.inputs
---

# Configure \<Functoid\> Functoid Dialog Box

 

Use the **Configure \<Functoid\> Functoid** dialog box to manage the input parameters to the selected functoid. Input parameters from records and fields in the source schema and from other functoids are established by dragging between the relevant items to create links that connect to the left side of the functoid. This dialog box enables you to add constant input parameters, change the order of input parameters (regardless of how they were created), and delete incorrect input parameters.


> [!NOTE]
> <P>If an input parameter to a functoid is not valid, a default value is passed to the functoid in its place. For numeric input parameters, the default value is zero (0). For all other input parameters, the default value is blank.</P>



## Input Parameters

Examine the existing ordered set of input parameters. Select an input parameter in this list to perform actions such as changing its position in the order or editing the constant value associated with the input parameter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Edit functoid constant</strong></td>
<td>Open the <strong>Functoid Constant Value</strong> dialog box to edit the value associated with a constant input parameter.<br />
<br />
When you initially add a constant input parameter, or double-click an existing constant input parameter, you can edit its value in place.</td>
</tr>
<tr class="even">
<td><strong>Insert new constant</strong></td>
<td>Insert a new constant input parameter at the end of the list of input parameters.<br />
<br />
Immediately after you click this button, you can begin editing the constant value.<br />
<br />
After inserting a new constant input parameter, you can use the up and down arrow buttons to move it to the proper location within the ordered list of input parameters.</td>
</tr>
<tr class="odd">
<td><strong>Delete selected input parameter</strong></td>
<td>Delete the selected input parameter from the ordered list of input parameters.</td>
</tr>
<tr class="even">
<td><strong>Move selected input parameter up</strong></td>
<td>Exchange the selected input parameter with the input parameter immediately above it in the ordered list, changing the order in which these parameters are passed to the corresponding functoid.</td>
</tr>
<tr class="odd">
<td><strong>Move selected input parameter down</strong></td>
<td>Exchange the selected input parameter with the input parameter immediately below it in the ordered list, changing the order in which these parameters are passed to the corresponding functoid.</td>
</tr>
<tr class="even">
<td><strong>Parameter count statement</strong></td>
<td>Examine the parameter count requirements of the current functoid. This statement is located immediately below the <strong>Input parameters</strong> list.</td>
</tr>
<tr class="odd">
<td><strong>Functoid description</strong></td>
<td>Read about the purpose and use of the functoid without needing to look at the online Help.</td>
</tr>
</tbody>
</table>


## See Also

[General Functoid Properties](general-functoid-properties.md)  
[How to Configure Functoid Input Parameters](https://msdn.microsoft.com/library/aa559380\(v=bts.80\))

