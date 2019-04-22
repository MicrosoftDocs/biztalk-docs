---
title: Data Type (Node Property of All Schemas)
TOCTitle: Data Type (Node Property of All Schemas)
ms:assetid: 46ead128-6cd1-4021-adfe-0a7f3a8f7e51
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559895(v=BTS.80)
ms:contentKeyID: 51527697
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Data Type (Node Property of All Schemas)

 

Use the **Data Type** property to:

  - Select an existing simple type to be associated with the selected **Field Element** or **Field Attribute** node.
    
    \- or -

  - Specify a name for an unnamed simple type associated with the selected **Field Element** or **Field Attribute** node, thereby converting its unnamed simple type to a global simple type.
    
    \- or -

  - Reference an existing global **Field Element** or **Field Attribute** node.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md), [Field Attribute](field-attribute-node-properties.md)

## Category

General

## Allowed Values

Any of the following, typed or chosen from the drop-down list:

  - An existing simple type to serve as the data type for the selected **Field Element** or **Field Attribute** node.

  - A unique string you provide to name your own derived simple type (typed only) so that it becomes a named global simple type and available for use in other **Field Element** or **Field Attribute** nodes. Other property fields, such as **Base Data Type**, **Derived By**, and potentially some properties from the **Restriction** category will need to be set first to create your own derived simple type.

  - The value of a **Node Name** property of an existing global **Field Element** or **Field Attribute** node that has been created as explicit child node of the **Schema** node. Global **Field Element** nodes will only be available in the drop-down list for **Field Element** nodes, and global **Field Attribute** nodes will only be available in the drop-down list for **Field Attribute** nodes.

## Default Value

**xs:string**

## XSD Persistence

When you choose an existing simple type, or type a new simple type name for this property, it is persisted as the value of **type** attribute of the element that corresponds to the selected **Field Element** or **Field Attribute** node.

When you choose to refer to an existing global **Field Element** or **Field Attribute** node, this property value is persisted as the value of the **ref** attribute of the element that corresponds to the selected **Field Element** or **Field Attribute** node.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor.

This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](https://msdn.microsoft.com/library/aa547363\(v=bts.80\)).

You can configure this property with data types such as **xs:string**, **xs:positiveInteger**, **xs:URI**, and so on.


> [!NOTE]
> <P>Storage in the message box truncates time values in <STRONG>xs:dateTime</STRONG> and <STRONG>xs:time</STRONG> elements below the millisecond level. A similar loss of precision may occur when converting to .NET date/time data types.</P>



## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

