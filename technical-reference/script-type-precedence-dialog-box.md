---
title: Script Type Precedence Dialog Box
TOCTitle: Script Type Precedence Dialog Box
ms:assetid: 3369245f-d8af-4046-80db-757d8fb4916b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559520(v=BTS.80)
ms:contentKeyID: 51527202
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.mapper.scripttype
---

# Script Type Precedence Dialog Box

 

Use the **Script Type Precedence** dialog box to configure the relative precedence of the various types of script that can be associated with a **Scripting** functoid.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Inline C#</strong></td>
<td>Configure whether inline C# code is relevant in the precedence order established in this dialog box. <strong>Note:</strong> Because the majority of functoids are written in C#, inline C# must remain enabled as an inline script language. Therefore, even if you clear the Inline C# check box, it will automatically become enabled again when you dismiss this dialog box.</td>
</tr>
<tr class="even">
<td><strong>External Assembly</strong></td>
<td>Configure whether code in external assemblies is relevant in the precedence order established in this dialog box.</td>
</tr>
<tr class="odd">
<td><strong>Inline Visual Basic .NET</strong></td>
<td>Configure whether inline Microsoft Visual Basic .NET code is relevant in the precedence order established in this dialog box.</td>
</tr>
<tr class="even">
<td><strong>Inline JScript .NET</strong></td>
<td>Configure whether inline Microsoft Visual JScript .NET code is relevant in the precedence order established in this dialog box.</td>
</tr>
<tr class="odd">
<td><strong>Inline XSLT Call Template</strong></td>
<td>Configure whether inline XSLT Call Template code is relevant in the precedence order established in this dialog box.</td>
</tr>
<tr class="even">
<td><strong>Inline XSLT</strong></td>
<td>Configure whether inline XSLT code is relevant in the precedence order established in this dialog box.</td>
</tr>
<tr class="odd">
<td><strong>Move selected script type up button</strong><br />
<br />
 <img src="images/Aa559520.d5832d06-555e-40a8-a959-ac49a9624ca8(BTS.80).jpeg" /></td>
<td>Exchange the selected script type with the script type immediately above it in the ordered list, increasing the relative precedence of the selected script type.</td>
</tr>
<tr class="even">
<td><strong>Move selected script type down button</strong><br />
<br />
 <img src="images/Aa559520.f5fb2199-f92e-40d6-be71-ee465fcc20d7(BTS.80).jpeg" /></td>
<td>Exchange the selected script type with the script type immediately below it in the ordered list, decreasing the relative precedence of the selected script type.</td>
</tr>
</tbody>
</table>


## See Also

[Configure Functoid Script Dialog Box](configure-functoid-script-dialog-box.md)  
[How to Configure the Scripting Functoid](https://msdn.microsoft.com/en-us/library/aa578238\(v=bts.80\))  
[Scripting Functoid](https://msdn.microsoft.com/en-us/library/aa561729\(v=bts.80\))

