---
title: Use XSL Transform (Grid Property)
TOCTitle: Use XSL Transform (Grid Property)
ms:assetid: 9e206d6d-55f4-41bf-a46a-29e33fe324fd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577606(v=BTS.80)
ms:contentKeyID: 51530003
ms.date: 12/27/2019
mtps_version: v=BTS.80
---

# Use XSL Transform (Grid Property)

Use the **Use XSL Transform** property to specify whether XslTransform will be used for XSLT transform or XslCompiledTransform. This property will only be used when ".Net Framework" is selected for "XSLT transform engine" property.

## Category

Compiler

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Undefined</td>
<td>Global level "Use XSL Transform" will be used if "Undefined" is selected.</td>
</tr>
<tr class="even">
<td>Yes</td>
<td>XslTransform will be used for XSLT transform.</td>
</tr>
<tr class="odd">
<td>No</td>
<td>XslCompiledTransform will be used for XSLT transform.</td>
</tr>
</tbody>
</table>

## Default Value

Undefined

## Remarks

Global level "Use XSL Transform" will be used if "Undefined" is selected for map level property. 
Find HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration hive in BizTalk Server registry, add new "DWORD Value" with name "UseXslTransform", value "1" means XslTransform will be used, otherwise "XslCompiedTransform" will be used. Default global "Use XSL Transform" is "0"(means XslCompiledTransform will be used) if this registry entry not exists.


> [!NOTE]
> <P>You cannot undo or redo the <STRONG>Use XSL Transform</STRONG> property.</P>



## See Also

[Grid Properties](grid-properties.md)

