---
title: "Simple Type Derivation Using the Union Mechanism | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e51ae390-78f5-4fb9-9163-2a8023aea1ec
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Simple Type Derivation Using the Union Mechanism
When you derive a new simple type from an existing simple type by using the union mechanism, you are specifying that the value for this attribute or element can be of more than one type, according to a list of types that you specify. For example, you can specify that an attribute or element value is either a date, a time, or a date/time value.  
  
 For comprehensive information about deriving new simple types by using the union mechanism, refer to the W3C website. For various links to this and other websites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 To derive a simple type as a union of several possible types, select the relevant **Field Element** node or **Field Attribute** node in the schema tree and then, in the Properties window, select a simple type from the drop-down list for the **Base Data Type** property. As soon as you have selected a value for this property, the **Derived By** property automatically changes from its default value to **Restriction**, which serves as the default value for type derivation. You must change the **Derived By** property from **Restriction** to **Union**, which causes the **Base Data Type** property to be renamed as the **Member Types** property (incidentally, the renamed property moves to a different position in the property list due to the alphabetical sorting of the properties).  
  
 Finally, you can use the check boxes in the **Member Types** drop-down checklist to select additional types to allow for corresponding values in instance messages.  
  
 When you first change a **Field Element** node or **Field Attribute** node from having a data type to having a base data type (thereby starting the process of simple type derivation), and then set the **Derived By** property to **Union**, you can observe the following change in the corresponding fragment in the XSD view.  
  
-   Before, with a newly inserted **Field Element** node named **DatesAndOrTimes**.  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
-   After setting the **Base Data Type** property to **xs:date**, and setting the **Derived By** property to **Union** (after which the **Base Data Type** property is renamed to be the **Member Types** property), and then also selecting **xs:datetime** and **xs:time** as additional allowed types in the **Member Types** drop-down checklist.  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
## See Also  
 [Simple Type Derivation](../core/simple-type-derivation.md)