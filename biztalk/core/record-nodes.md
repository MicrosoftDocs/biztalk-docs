---
title: "Record Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43af077d-5db8-43ca-8bd0-e3a9e3ebe2b0
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Record Nodes
In BizTalk Editor, you use a **Record** node to represent a collection of information, the individual items of which can be:  

- Simple types of information, such as strings and numbers, represented as child field nodes. These child field nodes can be either **Field Element** nodes or **Field Attribute** nodes. For additional information about these two types of field nodes, see [Field Element Nodes](../core/field-element-nodes.md) and [Field Attribute Nodes](../core/field-attribute-nodes.md).  

- Complex types of information, represented as child **Record** nodes or as a group node (**Sequence Group** node, **Choice Group** node, or **All Group** node).  

- Any unexamined type of information, represented as child **Any Element** or **Any Attribute** nodes.  

- Groups of attributes represented by an **Attribute Group** node.  

  When you insert a new child node into a **Record** node, the child node is always inserted at the end of the current child nodes. Within the XML Schema definition (XSD) language representation, new elements are added to the end of their corresponding areas, meaning that nonattribute elements are added to the end of the elements within the **sequence**, **choice**, **all**, or **group** element, and attribute elements are added to the end of any other attribute elements, all of which occur after the **sequence**, **choice**, **all**, or **group** element.  

## XSD representation  
 When first inserted, the XSD representation of a new **Record** node consists of only three lines, as shown in the following example.  

```  
<xs:element name="Record">  
      <xs:complexType />  
</xs:element>  
```  

 When any child node other than one of the three attribute nodes (**Field Attribute**, **Attribute Group**, and **Any Attribute**) is added to a **Record** node, by default it is placed within a **sequence** element within the **complexType** element. The **sequence** element is added when the first nonattribute child node is added, and removed if all the nonattribute child nodes are deleted. All three types of attribute nodes are added within the **complexType** element, but outside and after any **sequence** element.  

 The **sequence** element within which nonattribute child nodes are added can also be a **choice** or **all** element if you change the **Group Order Type (Node Property of All Schemas)** property of the corresponding node in the schema tree to **Choice** or **All**, respectively.  

 In the following example, the **Record** node has been renamed shipTo. The locations within the **Record** node where attribute and nonattribute nodes are added are shown in brackets.  

```  
<xs:element name="">  
    <xs:complexType>  
        <xs:sequence>  
            [Nonattribute child nodes of the record go here.]  
            [Always add new nonattribute child nodes to the end.]  
        </xs:sequence>  
            [Attribute child nodes of the record go here.]  
            [Always add new attribute child nodes to the end.]  
    </xs:complexType>  
</xs:element>  

```  

## See Also  
- [BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md)   
- [Node Properties](../core/node-properties.md)   
- **Record Node Properties** and **Group Order Type (Node Property of All Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
- [How to Set Node Properties](../core/how-to-set-node-properties.md)
