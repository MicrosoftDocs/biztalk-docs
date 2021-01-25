---
description: "Learn more about: XSLT Encoding (Grid Property)"
title: XSLT Encoding (Grid Property)
TOCTitle: XSLT Encoding (Grid Property)
ms:assetid: 9e206d6d-55f4-41bf-a46a-29e33fe324fd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577606(v=BTS.80)
ms:contentKeyID: 51530003
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# XSLT Encoding (Grid Property)

 

Use the **XSLT Encoding** property to specify the preferred character encoding that the parser should use to encode sequences of characters as sequences of bytes.

## Category

Custom Header

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
<td>None</td>
<td>Specifies that no value should be set for the <strong>encoding</strong> attribute of the <strong>&lt;xsl:output&gt;</strong> element.</td>
</tr>
<tr class="even">
<td>Hard-coded encoding choices in drop-down list</td>
<td>The drop-down list includes many common encoding choices, such as UTF-8.</td>
</tr>
<tr class="odd">
<td>Other valid encoding choices</td>
<td>Any freeform values that you type here are unverified by BizTalk Mapper. You must ensure their validity.</td>
</tr>
</tbody>
</table>


## Default Value

None

## Remarks

If you type a value for this property, it is treated case-insensitively; it must contain only printable ASCII characters and be a registered character set, or begin with x-.

This property provides a value for the **encoding** attribute of the XSL **output** element. For more information about this attribute, refer to the .NET Framework documentation.


> [!NOTE]
> <P>You cannot undo or redo the <STRONG>XSLT Encoding</STRONG> property.</P>



## See Also

[Grid Properties](grid-properties.md)

