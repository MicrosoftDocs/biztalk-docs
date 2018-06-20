---
title: "Attribute Group Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea02fae8-4e03-486a-8d9d-185ae230d3a0
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Attribute Group Nodes

## Overview
In BizTalk Editor, you can add an **Attribute Group** node to a **Record** node or to another **Attribute Group** node to contain a group of attributes that you expect to use in more than one **Record** node. Adding an **Attribute Group** node to another **Attribute Group** node achieves attribute group nesting. This allows you to define a group of attributes in one place that can be used in multiple **Record** or **Attribute Group** nodes. Subsequent modifications to the attribute group will propagate to all of the nodes with which that attribute group is associated. This is true regardless of the node context in which the modifications are made.  

> [!NOTE]
>  In BizTalk Editor, the **AttributeGroup** node is represented by default with the string \<AttribGroup:attribGroup*N*\> in the schema tree view, where *N* is a monotonically increasing numeral. You can change the attribGroup*N* portion of its name by typing a new unique name in its **Group Reference** property.  

 When initially creating an **Attribute Group** node, you simply insert it into one of the **Record** or **Attribute Group** nodes in which it will be used, and optionally change its name in its **Group Reference** property. There are two ways to use the same attribute group in another **Record** or **Attribute Group** node:  

- You can copy the existing **Attribute Group** node and then paste it into that other **Record** node.  

- You can insert a new **Attribute Group** node into that other **Record** node, and then set the **Group Reference** property of the new **Attribute Group** node to reference an existing **Attribute Group** node.  

  Thereafter, you can modify the **Attribute Group** node—for example, by adding or deleting a **Field Attribute** node—in the context of any **Record** or **Attribute Group** node into which you pasted it. That change will propagate to all other **Record** or **Attribute Group** nodes with which the attribute group is associated.  

  It would be pointless to add an **Attribute Group** node without adding at least one relevant node to it, where relevant nodes include **Field Attribute** nodes, **Any Attribute** nodes, and (nested) **Attribute Group** nodes. In fact, an attribute group that contains only a single attribute is somewhat ill-conceived, unless you are making a point of planning for the addition of more attributes in the future.  

  **Attribute Group** nodes can be nested, allowing more possibilities in how groups of attributes can be constructed and combined. **Attribute Group** nodes can also contain the **Any Attribute** node, allowing an attribute group to contain wildcard character capabilities with respect to the attribute instances it can accommodate.  

## XSD representation  
 When an **Attribute Group** node is first added to a **Record** node or to another **Attribute Group** node, two distinct areas of the corresponding XML Schema definition (XSD) language representation of the schema are affected. In the following example, a new **Attribute Group** node, in bold, has been added to an existing **Record** node that already contains an existing **Field Element** node.  

```  
        ...  
        <xs:element name="ExistingRecord">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ExistingFieldElement" type="xs:string" />  
                </xs:sequence>  
                <xs:attributeGroup ref="attrGroup0" />  
            </xs:complexType>  
        </xs:element>  
        ...   
    <xs:attributeGroup name="attrGroup0" />  
</xs:schema>  
```  

 Note how the **attributeGroup** element within the XSD representation of the **Record** node references a global **attributeGroup** element that is added as a child of the **schema** element. This global definition of the attribute group within the XSD representation of the schema allows the attribute group to be referenced in multiple locations throughout the schema.  

> [!NOTE]
>  Default attribute group names that are supplied automatically have the form attrGroup*N*, where *N* is a monotonically increasing numeral. You can rename an attribute group by providing a new, unique name in its **Group Reference** property. An attribute group cannot be renamed in place within the schema tree.  

## See Also  
- [BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md)   
- [Node Properties](../core/node-properties.md)   
- **Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
- [How to Set Node Properties](../core/how-to-set-node-properties.md)   
- [Field Attribute Nodes](../core/field-attribute-nodes.md)   
- [Any Attribute Nodes](../core/any-attribute-nodes.md)
