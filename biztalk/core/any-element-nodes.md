---
title: "Any Element Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7e30fcf-31bc-4d48-9bc7-0be90e927127
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Any Element Nodes
In BizTalk Editor, you can use an **Any Element** node to indicate a location within an instance message where unknown elements may appear. This accommodates situations in which you know that some element might appear at a particular location within an instance message, but you do not know the name of the element, or how complicated it might be. If you place an **Any Element** node at the appropriate location within the schema, BizTalk can process such unknown portions of a message. The only requirement is that the corresponding XML is well-formed.  
  
> [!NOTE]
>  In BizTalk Editor, the **Any Element** node is represented with the string \<Any\> in the schema tree view.  
> 
> [!NOTE]
>  You can control the degree to which the unknown portion of the message is validated as well-formed XML by using the **Process Contents** property. In many cases you may need to set the **Process Contents** property to **Skip** for the contents of an instance message at the location of the **Any Element** node to be processed. Retaining the default value of **Strict** for the **Process Contents** property will prevent instance message validation from passing.  
> 
> More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## XSD representation  
 When an **Any Element** node is added to a **Record** node, or to another node to which it can be added such as a **Sequence Group**, **Choice Group**, or **All Group** node, a single XML tag is added to the corresponding XML Schema definition (XSD) language representation of the schema. In the following example, a new **Any Element** node, whose XSD representation is shown in bold type, has been added to an existing **Record** node that already contains a **Field Element** node.  
  
```  
<xs:element name="ExistingRecord">  
    <xs:complexType>  
        <xs:sequence>  
             <xs:element name="ExistingFieldElement" type="xs:string" />  
            <xs:any />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
```  
  
 Assuming that the **Process Contents** property of the **Any Element** node is set to **Skip**, within an instance message governed by this schema fragment, an **ExistingRecord** element is expected to contain an **ExistingFieldElement** element containing string data, followed by any single element of arbitrary complexity.  
  
## See Also  
 [BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md)   
 [Node Properties](../core/node-properties.md)   
 [How to Set Node Properties](../core/how-to-set-node-properties.md)   
 [Any Attribute Nodes](../core/any-attribute-nodes.md)