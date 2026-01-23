---
description: "Learn more about: Ignore Namespaces for Links (Grid Property)"
title: Ignore Namespaces for Links (Grid Property)
TOCTitle: Ignore Namespaces for Links (Grid Property)
ms:assetid: a139416b-da76-4aa8-9058-0c3979a39bb9
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577689(v=BTS.80)
ms:contentKeyID: 51530154
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Ignore Namespaces for Links (Grid Property)


Use the **Ignore Namespaces for Links** property to indicate whether the links stored in the map contain any references to the namespaces used in the schemas.

## Category

General

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Drop-down list choice</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>True</strong></td>
<td>Specifies that the links in the map do not contain any references to the namespaces used in the source or destination schemas, thereby protecting the links from changes made to those schema namespaces outside the map.</td>
</tr>
<tr class="even">
<td><strong>False</strong></td>
<td>Specifies that the links in the map contain references to the namespaces used in the source and destination schemas, thereby making the links sensitive to changes made to those schema namespaces outside the map.</td>
</tr>
</tbody>
</table>


## Default Value

**True**

## Remarks

If the value of this property is set to **True**, changes to the namespaces in the source and destination schemas used by the map will not invalidate its links.

The only situation in which you should set the value of this property to **False** is when either your source or destination schema contains sibling nodes of the same type and with the same name, but with different namespaces. In such cases, the namespace designator in links is necessary to find the correct source or destination node for the link in the produced XSLT.


> [!NOTE]
> <P>You can undo or redo the <STRONG>Ignore Namespaces for Links</STRONG> property.</P>



## See Also

[Grid Properties](grid-properties.md)

