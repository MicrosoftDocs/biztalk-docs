---
title: Derived By (Node Property of All Schemas)
TOCTitle: Derived By (Node Property of All Schemas)
ms:assetid: d9b89527-6611-4cc6-af58-e2e6334f8b0d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578709(v=BTS.80)
ms:contentKeyID: 51531659
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Derived By (Node Property of All Schemas)

 

Use the **Derived By** property to define whether the data type being derived for the currently selected **Record**, **Field Element**, or **Field Attribute** node is an extension, restriction, list, or union of the type specified by the **Base Data Type** property.

## Applies to Nodes of Type

[Record](record-node-properties.md), [Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

Advanced

## Allowed Values

The following table shows the choices for this property when a **Record** node is selected.

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
<td>Use this value to return to the default behavior: the data type of the selected <strong>Record</strong> node is not derived from another type.</td>
</tr>
<tr class="even">
<td><strong>Extension</strong></td>
<td>Use this value to derive a new, extended data type from the simple or complex data type defined by the <a href="content-type-node-property-of-all-schemas.md">Content Type</a> and <a href="base-data-type-node-property-of-all-schemas.md">Base Data Type</a> properties.</td>
</tr>
<tr class="odd">
<td><strong>Restriction</strong></td>
<td>Use this value to derive a new, restricted data type from the simple or complex data type defined by the <strong>Content Type</strong> and <strong>Base Data Type</strong> properties.</td>
</tr>
</tbody>
</table>


The following table shows the choices for this property when a **Field Element** or **Field Attribute** node is selected.

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
<td>Use this value to return to the default behavior: the data type of the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node is not derived from another type.</td>
</tr>
<tr class="even">
<td><strong>Restriction</strong></td>
<td>Use this value to derive a new, restricted data type from the simple data type defined by the <strong>Content Type</strong> and <strong>Base Data Type</strong> properties.<br />
<br />
When you specify this value, all of the properties in the <strong>Restricted</strong> category become available for contriving a specific set of data restrictions.</td>
</tr>
<tr class="odd">
<td><strong>List</strong></td>
<td>Use this value to specify that instance message data that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node can be a list of white-space separated values of the data type specified by the <a href="item-type-node-property-of-all-schemas.md">Item Type</a> property.<br />
<br />
Use caution when the <strong>Base Data Type</strong> property specifies &quot;xs:string&quot; because strings can themselves contain white space which introduces ambiguity into the data.</td>
</tr>
<tr class="even">
<td><strong>Union</strong></td>
<td>Use this value to specify that the instance message data that corresponds to the selected <strong>Field Element</strong> or <strong>Field Attribute</strong> node can be one of several different data types, as specified by the <a href="member-types-node-property-of-all-schemas.md">Member Types</a> property.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, indicating that the data type of the currently selected **Record**, **Field Element**, or **Field Attribute** node is not derived from another data type.

## XSD Persistence

The XSD persistence of the **Derived By**, **Base Data Type**, **Content Type** (**Record** nodes only), **Item Type**, and **Member Types** properties are interrelated, as shown in the following table.

<table>
<thead>
<tr class="header">
<th>Node type and property settings</th>
<th>XSD persistence</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Record</strong> node with:<br />
<br />
 <strong>Derived By</strong> = <strong>Extension</strong><br />
<br />
 <strong>Content Type</strong> = <strong>SimpleContent</strong></td>
<td>&lt;element&gt;<br />
<br />
&lt;complexType&gt;<br />
<br />
&lt;simpleContent&gt;<br />
<br />
&lt;extension base=&quot;<em>BDT</em>&quot;&gt;<br />
<br />
where &quot;<em>BDT</em>&quot; is the value of the <strong>Base Data Type</strong> property.</td>
</tr>
<tr class="even">
<td><strong>Record</strong> node with:<br />
<br />
 <strong>Derived By</strong> = <strong>Extension</strong><br />
<br />
 <strong>Content Type</strong> = <strong>ComplexContent</strong></td>
<td>&lt;element&gt;<br />
<br />
&lt;complexType&gt;<br />
<br />
&lt;complexContent&gt;<br />
<br />
&lt;extension base=&quot;&lt;<em>Base Data Type</em>&gt;&quot;</td>
</tr>
<tr class="odd">
<td><strong>Record</strong> node with:<br />
<br />
 <strong>Derived By</strong> = <strong>Restriction</strong><br />
<br />
 <strong>Content Type</strong> = <strong>SimpleContent</strong></td>
<td>&lt;element&gt;<br />
<br />
&lt;complexType&gt;<br />
<br />
&lt;simpleContent&gt;<br />
<br />
restriction base=&quot;<em>BDT</em>&quot;&gt;<br />
<br />
where &quot;<em>BDT</em>&quot; is the value of the <strong>Base Data Type</strong> property.</td>
</tr>
<tr class="even">
<td><strong>Record</strong> node with:<br />
<br />
 <strong>Derived By</strong> = <strong>Restriction</strong><br />
<br />
 <strong>Content Type</strong> = <strong>ComplexContent</strong></td>
<td>&lt;element&gt;<br />
<br />
&lt;complexType&gt;<br />
<br />
&lt;complexContent&gt;<br />
<br />
&lt;restriction base=&quot;<em>BDT</em>&quot;&gt;<br />
<br />
where &quot;<em>BDT</em>&quot; is the value of the <strong>Base Data Type</strong> property.</td>
</tr>
<tr class="odd">
<td><strong>Field Element</strong> or <strong>Field Attribute</strong> node with:<br />
<br />
 <strong>Derived By</strong> = <strong>Restriction</strong></td>
<td>&lt;element&gt; or &lt;attribute&gt;, respectively<br />
<br />
&lt;simpleType&gt;<br />
<br />
&lt;restriction base=&quot;<em>BDT</em>&quot;&gt;<br />
<br />
where &quot;<em>BDT</em>&quot; is the value of the <strong>Base Data Type</strong> property.</td>
</tr>
<tr class="even">
<td><strong>Field Element</strong> or <strong>Field Attribute</strong> node with:<br />
<br />
 <strong>Derived By</strong> = <strong>List</strong></td>
<td>&lt;element&gt; or &lt;attribute&gt;, respectively<br />
<br />
&lt;simpleType&gt;<br />
<br />
&lt;list itemType=&quot;<em>IT</em>&quot;&gt;<br />
<br />
where &quot;<em>IT</em>&quot; is the value of the <strong>Item Type</strong> property.</td>
</tr>
<tr class="odd">
<td><strong>Field Element</strong> or <strong>Field Attribute</strong> node with:<br />
<br />
 <strong>Derived By</strong> = <strong>Union</strong></td>
<td>&lt;element&gt; or &lt;attribute&gt;, respectively<br />
<br />
&lt;simpleType&gt;<br />
<br />
&lt;union memberTypes=&quot;<em>MTs</em>&quot;&gt;<br />
<br />
where &quot;<em>MTs</em>&quot; is the value of the <strong>Member Types</strong> property.</td>
</tr>
</tbody>
</table>


## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Record** (including a root **Record** node), **Field Element**, or **Field Attribute** node in BizTalk Editor.

The setting of this property interacts with the **Base Data Type**, **Content Type** (**Record** nodes only), **Item Type**, and **Member Types** properties.

For **Field Element** and **Field Attribute** nodes (not for **Record** nodes), if you set the **Derived By** property to **Restriction**, the following properties, which represent **simpleType** facets in XSD, become available for you to edit:

  - [Enumeration](enumeration-node-property-of-all-schemas.md)

  - [Length](length-node-property-of-all-schemas.md)

  - [MaxFacet Type](maxfacet-type-node-property-of-all-schemas.md)

  - [MaxFacet Value](maxfacet-value-node-property-of-all-schemas.md)

  - [Maximum Length](maximum-length-node-property-of-all-schemas.md)

  - [MinFacet Type](minfacet-type-node-property-of-all-schemas.md)

  - [MinFacet Value](minfacet-value-node-property-of-all-schemas.md)

  - [Minimum Length](minimum-length-node-property-of-all-schemas.md)

  - [Pattern](pattern-node-property-of-all-schemas.md)

When you change the value of the [Derived By (Node Property of All Schemas) \[BTS05\]](derived-by-node-property-of-all-schemas.md) property, any value associated with the [Fixed](fixed-node-property-of-all-schemas.md) or the [Default Value](default-value-node-property-of-all-schemas.md) property is deleted (they cannot both have a value). As appropriate, you must provide a new value for the **Fixed** or **Default Value** property that conforms to the chosen **Base Data Type** and (new) **Derived By** property settings.

Moreover, you cannot set the **Derived By** property to **Extension** to derive from *xs:anyType* otherwise you may receive an error message as in the below Note section. To correct this error, you can either change **Derived By** property to **Restriction** or change the **Base Data Type** from *xs:anyType* to some other type.


> [!NOTE]
> <P>Wildcard '##any' allows element 'ACTUAL_FIELD_NAME', and causes the content model to become ambiguous. A content model must be formed such that during validation of an element information item sequence, the particle contained directly, indirectly or implicitly therein with which to attempt to validate each item in the sequence in turn can be uniquely determined without examining the content or attributes of that item, and without any information about the items in the remainder of the sequence.</P>



For more information about different types of derivations, see [Type Reuse and Derivations](https://msdn.microsoft.com/en-us/library/aa559208\(v=bts.80\)).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

