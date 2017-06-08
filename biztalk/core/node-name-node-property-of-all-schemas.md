---
title: "Node Name (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Node Name property [schemas]"
ms.assetid: 32930e41-ce2a-4161-9696-e5865099ac9a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Node Name (Node Property of All Schemas)
Use the **Node Name** property to display the name of the node as it appears in the schema tree view in BizTalk Editor, and for some types of nodes, to change the name of the node to describe its content.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md), [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md), [Sequence Group](../core/sequence-group-node-properties.md), [Choice Group](../core/choice-group-node-properties.md), [All Group](../core/all-group-node-properties.md), [Attribute Group](../core/attribute-group-node-properties.md), [Any Element](../core/any-element-node-properties.md), [Any Attribute](../core/any-attribute-node-properties.md), [Equivalent](../core/equivalent-node-properties.md), [Equivalent Child](../core/equivalent-child-node-properties.md)  
  
## Category  
 General  
  
## Allowed Values  
 Node names must conform to the name requirements of XSD and XML. For those nodes for which the **Node Name** property value can be changed, if you type a node name that does not conform to these requirements, you will be prompted with the following choices:  
  
-   Encode the nonconforming name so that it conforms to XSD/XML requirements.  
  
-   Cancel the naming operation and roll back to the previous name.  
  
 For information about the encoding scheme used by BizTalk Editor to encode non-XML characters, see the .NET Framework documentation for the **EncodeLocalName** method of the **System.Xml.XmlConvert** class. BizTalk Editor uses the same encoding scheme.  
  
 Two common situations that require encoding are a leading numeral and the space character.  
  
## Default Value  
 The **Node Name** property has different default values for different types of nodes, as follows:  
  
|Node type|Node name default values|  
|---------------|------------------------------|  
|**Schema**|\<Schema>|  
|**Record**|Record|  
|**Field Element**|Field|  
|**Field Attribute**|Field|  
|**Sequence Group**|\<Sequence>|  
|**Choice Group**|\<Choice>|  
|**All Group**|\<All>|  
|**Attribute Group**|\<AttrGroup:attrGroup*N*><br /><br /> where "*N*" is a monotonically increasing number starting at zero (0)|  
|**Any Element**|\<Any>|  
|**Any Attribute**|\<AnyAttribute>|  
|**Equivalent**|\<Equivalent>|  
|**Equivalent Child**|The names of the base complex type and set of derived complex types, displayed within angle brackets (\<type>), associated with the containing **Equivalent** node.|  
  
## XSD Persistence  
 The **Node Name** property is persisted differently in the XSD for different types of nodes, as follows:  
  
|Node type|Node name XSD persistence|  
|---------------|-------------------------------|  
|**Schema**|As the **schema** element.|  
|**Record**|As the value of the **name** attribute of the corresponding **element** element.|  
|**Field Element**|As the value of the **name** attribute of the corresponding **element** element.|  
|**Field Attribute**|As the value of the **name** attribute of the corresponding **attribute** element.|  
|**Sequence Group**|When the **Group Reference** property has no value, as a **sequence** element.<br /><br /> When the **Group Reference** property has a value, the variable portion of the node name, which follows the leading "Group:" substring, is persisted as the **ref** attribute of the instances of the usage of the sequence group and as the **name** attribute of the global definition of the sequence group.|  
|**Choice Group**|When the **Group Reference** property has no value, as a **choice** element.<br /><br /> When the **Group Reference** property has a value, the variable portion of the node name, which follows the leading "Group:" substring, is persisted as the **ref** attribute of the instances of the usage of the choice group and as the **name** attribute of the global definition of the choice group.|  
|**All Group**|When the **Group Reference** property has no value, as an **all** element.<br /><br /> When the **Group Reference** property has a value, the variable portion of the node name, which follows the leading "Group:" substring, is persisted as the **ref** attribute of the instances of the usage of the all group and as the **name** attribute of the global definition of the all group.|  
|**Attribute Group**|The variable portion of the node name, which follows the leading "AttrGroup:" substring, is persisted as the **ref** attribute of the instances of the usage of the attribute group and as the **name** attribute of the global definition of the attribute group.|  
|**Any Element**|As an **any** element.|  
|**Any Attribute**|As an **anyAttribute** element.|  
|**Equivalent** and **Equivalent Child**|**Equivalent** and **Equivalent Child** nodes are BizTalk Editor constructs and are not part of the XSD standard. These nodes exist to help you visualize the inheritance that is present among the base types and derived types in the schema.|  
  
## Remarks  
 You can examine this property, and in some cases set this property, in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a node in BizTalk Editor.  
  
 The **Node Name** property behaves differently for different types of nodes, as follows:  
  
|Node type|Node name property behavior|  
|---------------|---------------------------------|  
|**Schema**|Read-only. It is always set to "\<Schema>".|  
|**Record**, **Field Element**, and **Field Attribute**|Read/write. You can rename **Record**, **Field Element**, and **Field Attribute** nodes using the **Node Name** property, or in-place within the schema tree when you first insert them or when you use the **Rename** command on the shortcut menu for the node.<br /><br /> Sibling **Record** and **Field Element** nodes from the same namespace can only have the same **Node Name** property value if they have the same data type (except when it is a global declaration), and sibling **Field Attribute** nodes from the same namespace can never have the same **Node Name** property value.|  
|**Sequence Group**, **Choice Group**, and **All Group**|Read-only. However, any nonblank value in the corresponding [Group Reference](../core/group-reference-node-property-of-all-schemas.md) property contributes to the **Node Name** property value for these element group nodes. For example, if you set the **Group Reference** property to the value "BillingAddress", the **Node Name** property will become "Group:BillingAddress".|  
|**Attribute Group**|Read-only. However, the value in the corresponding [Group Reference](../core/group-reference-node-property-of-all-schemas.md) property, whether the default value or a value you provide, contributes to the **Node Name** property value for **Attribute Group** nodes. For example, if you set the **Group Reference** property to the value "ProductDimensions", the **Node Name** property will become "AttrGroup:ProductDimensions".|  
|Any Element|Read-only. It is always set to "\<Any>".|  
|Any Attribute|Read-only. It is always set to "\<AnyAttribute>".|  
|Equivalent|Read-only. It is always set to "\<Equivalent>".|  
|Equivalent Child|Read-only. It is always set to one of the complex type names associated with the parent **Equivalent** node, either the base complex type name or one of the derived complex type names.|  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)