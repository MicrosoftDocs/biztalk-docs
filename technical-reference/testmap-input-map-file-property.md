---
title: TestMap Input (Map File Property)
TOCTitle: TestMap Input (Map File Property)
ms:assetid: ad11b72e-c9c1-4589-8f87-461cbf70e2c6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578041(v=BTS.80)
ms:contentKeyID: 51530489
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# TestMap Input (Map File Property)

 

Use the **TestMap Input**property to specify the format of the input instance message specified by the **TestMap Input Instance** property, or to specify that you want to automatically generate an input instance message to use for testing the map.

## Category

Test Map

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
<td><strong>Generate Instance</strong></td>
<td>Use this value if you want an instance message to be generated automatically in the course of testing the map.</td>
</tr>
<tr class="even">
<td><strong>XML</strong></td>
<td>Use this value if the format of the input instance message specified by the <strong>TestMap Input Instance</strong> property is XML.</td>
</tr>
<tr class="odd">
<td><strong>Native</strong></td>
<td>Use this value if the format of the input instance message specified by the <strong>TestMap Input Instance</strong> property is a native format, such as a flat file format, as specified by the source schema associated with the map.</td>
</tr>
</tbody>
</table>


## Default Value

**Generate Instance**

## Remarks

If you specify a custom input instance message by using the **TestMap Input Instance** property, you must choose **XML** or **Native** as the value for this property. For more information, see [TestMap Input Instance (Map File Property)](testmap-input-instance-map-file-property.md).

## See Also

[Map File Properties](map-file-properties.md)

