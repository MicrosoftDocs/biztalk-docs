---
description: "Learn more about: Configure Functoid Script Dialog Box"
title: Configure Functoid Script Dialog Box
TOCTitle: Configure Functoid Script Dialog Box
ms:assetid: 696dc165-0452-4b5b-83f4-2cbe814f175b
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560603(v=BTS.80)
ms:contentKeyID: 51528649
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.mapper.functiod.script
---

# Configure Functoid Script Dialog Box

 

Use the **Configure Functoid Script** dialog box to either identify or provide the code to be associated with the selected **Scripting** functoid.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Script Type</strong></td>
<td>Select this <strong>Scripting</strong> functoid as relying on an external assembly for its code, or select one of the available inline languages in which to provide your code within this dialog box. <strong>Important:</strong> When you switch from one inline language to another, any script you have written for the language you are switching from is not deleted. You must either delete that script manually, or ensure that your new language choice has a higher precedence than your old language choice using the <a href="script-type-precedence-dialog-box.md">Script Type Precedence Dialog Box</a>.</td>
</tr>
<tr class="even">
<td><strong>Script Assembly</strong></td>
<td>When <strong>Script Type</strong> has been set to External Assembly, select the assembly that contains the method to be used as the code for this functoid.</td>
</tr>
<tr class="odd">
<td><strong>Script Class</strong></td>
<td>When <strong>Script Type</strong> has been set to External Assembly, select the class within the selected assembly that contains the method to be used as the code for this functoid.</td>
</tr>
<tr class="even">
<td><strong>Script Method</strong></td>
<td>When <strong>Script Type</strong> has been set to External Assembly, select the method within the selected assembly and class to be used as the code for this functoid.</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
</tbody>
</table>


## See Also

[Script Type Precedence Dialog Box](script-type-precedence-dialog-box.md)  
[How to Configure the Scripting Functoid](https://msdn.microsoft.com/library/aa578238\(v=bts.80\))  
[Scripting Functoid](https://msdn.microsoft.com/library/aa561729\(v=bts.80\))

