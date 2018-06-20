---
title: "All Group Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e28d98c-746a-44d8-bed2-ba539b8432aa
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# All Group Nodes
In BizTalk Editor, you can insert an **All Group** node to contain other nodes that will appear zero or one time, in any order. In XML Schema definition (XSD) language, the **All group** has more usage limitations than **Sequence** and **Choice** groups, which translates to few situations within BizTalk Editor where you will be able to create an **All Group** node.  

 To use an **All Group** node in BizTalk Editor, you need to follow some extra steps: The easiest way to create an **All Group** node is to change the value of the **Group Order Type** property of the parent **Record** node to **All**. This ensures that all of the subordinate nodes of the **Record** node are contained within the **All Group** node.  See **Group Order Type** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

 Another way to use an **All Group** node in BizTalk Editor begins with inserting a new **Record** node. After inserting the new **Record** node, change its **Content Type** property to **ComplexContent**. Then you can insert an **All Group** node as a child of the **Record** node. This is required because the **All Group** can only be inserted when inheritance is involved. By specifying that the containing **Record** node contains complex content, its data type becomes based on the data type **xs:anyType**, derived by extension.  

> [!NOTE]
>  In BizTalk Editor, the **All Group** node is represented with the string \<All> in the schema tree view. If you set a reference to an **All Group** node, such as to x, it is represented as \<Group:x> in the schema tree view.  

## XSD representation  
 An **All Group** node can be inserted into a **Record** node, but only if it is the only non-attribute child node of that **Record** node. The following example shows, in steps, how a new **All Group** node is represented in the XML Schema definition (XSD) language as an **all** element as the steps in BizTalk Editor are performed (with nodes named to clarify their identity).  

```  
<xs:element name="NewRecord">  
    <xs:complexType />   
</xs:element>  
```  

 After adding a new record as shown in the preceding XSD fragment, its **Content Type** property is changed to **ComplexContent**, resulting in the following XSD modifications.  

```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
             <xs:extension base="xs:anyType" />  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  

 Now the **All Group** node can be inserted as a child of the new record, as shown in the following XSD fragment.  

```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
            <xs:extension base="xs:anyType">  
                <xs:all />   
             </xs:extension>  
          </xs:complexContent>  
     </xs:complexType>  
</xs:element>  
```  

 Finally, you can insert appropriate nodes as children of the new **All Group** node. The following example shows a **Record** node and a **Field Element** node inserted as child nodes of the new **All Group** node.  

```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
            <xs:extension base="xs:anyType">  
                <xs:all>  
                    <xs:element name="RecordChildOfAllGroup">  
                        <xs:complexType />  
                    </xs:element>  
                    <xs:element name="FieldElementChildOfAllGroup" type="xs:string" />  
                </xs:all>  
            </xs:extension>  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  

## See Also  
- [BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md)   
- [Node Properties](../core/node-properties.md)   
- **Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] 
- [How to Set Node Properties](../core/how-to-set-node-properties.md)
