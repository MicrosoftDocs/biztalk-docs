---
title: Mixed (Node Property of All Schemas)
TOCTitle: Mixed (Node Property of All Schemas)
ms:assetid: a7823467-992e-40cf-9f82-2fba22a157c9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577926(v=BTS.80)
ms:contentKeyID: 51530333
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Mixed (Node Property of All Schemas)

 

Use the **Mixed** property to specify that character data or text might appear mixed with subelements within the element corresponding to the selected **Record** node in instance messages.

## Applies to Nodes of Type

[Record](record-node-properties.md)

## Category

Advanced

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
<td>Sets the <strong>mixed</strong> attribute of the <strong>complexType</strong> element to &quot;true&quot;, specifying that the corresponding content in an instance message will be mixed; that is substructure and content can both occur.</td>
</tr>
<tr class="even">
<td><strong>False</strong></td>
<td>Removes the <strong>mixed</strong> attribute of the <strong>complexType</strong> element, specifying that the instance messages corresponding to the selected <strong>Record</strong> node will have either substructure or content, but not both.</td>
</tr>
</tbody>
</table>


## Default Value

**False**, specifying that the instance messages corresponding to the selected **Record** node will have either substructure or content, but not both.

## XSD Persistence

As the value of the **mixed** attribute of the **complexType** element that is a child of the element that corresponds to the selected **Record** node.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** node, including root **Record** nodes, in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/en-us/library/aa547363\(v=bts.80\)).

HTML provides a very common example of mixed substructure and content. The paragraph tags in the following HTML example contain mixed content:

\<P\>The full moon \<EM\>always\</EM\> rises at sunset, more or less.\</P\>

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

