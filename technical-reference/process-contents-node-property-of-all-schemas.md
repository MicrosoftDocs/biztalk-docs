---
title: Process Contents (Node Property of All Schemas)
TOCTitle: Process Contents (Node Property of All Schemas)
ms:assetid: 0e1660e6-e2f5-402c-88ca-5fda990eb855
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547371(v=BTS.80)
ms:contentKeyID: 51526206
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Process Contents (Node Property of All Schemas)

 

Use the **Process Contents** property to specify the level of validation for the selected **Any Element** or **Any Attribute** node.

## Applies to Nodes of Type

[Any Element](any-element-node-properties.md), [Any Attribute](any-attribute-node-properties.md)

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
<td><strong>(Default)</strong></td>
<td>Use this to clear the property field of other values and to remove the <strong>processContents</strong> attribute from the corresponding <strong>any</strong> or <strong>anyAttribute</strong> element in the XSD representation. When you select this option, the default behavior associated with the <strong>Strict</strong> setting is used.</td>
</tr>
<tr class="even">
<td><strong>Lax</strong></td>
<td>Specifies that validation should be loosely applied to the elements or attributes found in the position of the corresponding <strong>any</strong> or <strong>anyAttribute</strong> element, respectively, in the XSD representation by setting its <strong>processContents</strong> attribute to &quot;lax&quot;. With this setting, validation is only performed if the corresponding element or attribute declaration is found in the schema.</td>
</tr>
<tr class="odd">
<td><strong>Skip</strong></td>
<td>Specifies that validation should not occur for the elements found in the position of the corresponding <strong>any</strong> or <strong>anyAttribute</strong> element, respectively, in the XSD representation by setting its <strong>processContents</strong> attribute to &quot;skip&quot;.</td>
</tr>
<tr class="even">
<td><strong>Strict</strong></td>
<td>Specifies that validation should be strictly applied to the elements found in the position of the corresponding <strong>any</strong> or <strong>anyAttribute</strong> element, respectively, in the XSD representation by setting its <strong>processContents</strong> attribute to &quot;strict&quot;.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, resulting in the behavior associated with the **Strict** setting.

## XSD Persistence

As the value of the **processContents** attribute of the corresponding **any** or **anyAttribute** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select an **Any Element** or **Any Attribute** node in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

You should generally set this property value to **Skip** to successfully validate XML documents containing elements that are represented by the corresponding **Any Element** or **Any Attribute** node. Other setting combinations are summarized in the table below:

<table>
<thead>
<tr class="header">
<th>&lt;xs:any&gt; Setting</th>
<th>Intent</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>&lt;xs:any processContents=&quot;strict&quot;/&gt;</td>
<td>Allow any element from any namespace with strict validation.</td>
<td>You must import the different schemas that may appear as an element. If you do not, validation will fail because the element is not declared.</td>
</tr>
<tr class="even">
<td>&lt;xs:any processContent=&quot;lax&quot;/&gt;</td>
<td>Allow any element from any namespace with lax validation.</td>
<td>Elements belonging to schemas that have been imported will be validated while all others will be skipped. If you forget to import a schema, validation will succeed.</td>
</tr>
<tr class="odd">
<td>&lt;xs:any processContent=&quot;skip&quot;/&gt;</td>
<td>Allow any element from any namespace skipping any validation.</td>
<td>Validation for all elements will be skipped.</td>
</tr>
<tr class="even">
<td>&lt;xs:any processContents=&quot;strict&quot; namespace=&quot;http://mynamespace&quot;/&gt;</td>
<td>Allow elements from a specific namespace with strict validation.</td>
<td>You must import the schemas that may appear as an element. If you do not, validation will fail because the element is not declared.</td>
</tr>
<tr class="odd">
<td>&lt;xs:any processContents=&quot;strict&quot; namespace=&quot;##Other&quot;/&gt;</td>
<td>Allow elements from any schema other than the one containing this &lt;xs:any&gt; tag.</td>
<td>You must import the schemas that may appear as an element. If you do not, validation will fail because the element is not declared.</td>
</tr>
<tr class="even">
<td>&lt;xs:any processContents=&quot;strict&quot; namespace=&quot;http://mynamespace &quot;<br />
<br />
minOccurs=&quot;1&quot; maxOccurs=&quot;50&quot;/&gt;</td>
<td>Allow 1 to 50 elements from a specific namespace with strict validation.</td>
<td>You must import the schemas that may appear as an element. If you do not, validation will fail because the element is not declared.</td>
</tr>
</tbody>
</table>


There are some combinations of elements that, when used with the **Any** element, may cause the content model to become ambiguous. For example, if your schema contains an element with a maxOccurs constraint prior to an **Any** element, you must qualify the **Any** element with a namespace:

```C#
<xs:element ref="ns0:Automobile" maxOccurs="10"/>  
<xs:any namespace="http://mynamespace" processContents="lax"/>   
```


> [!NOTE]
> <P>Make sure you understand the impact of the <STRONG>Any</STRONG> element within your schema and make accommodations as needed.</P>



## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

