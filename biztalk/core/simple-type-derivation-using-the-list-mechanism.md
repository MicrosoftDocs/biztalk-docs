---
description: "Learn more about: Simple Type Derivation Using the List Mechanism"
title: "Simple Type Derivation Using the List Mechanism | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14f3c7b7-7585-4297-9177-2deaef8355f0
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Simple Type Derivation Using the List Mechanism
When you derive a new simple type from an existing simple type by using the list mechanism, you are specifying that the value for this attribute or element can be a space-separated list of values of the specified type. For example, you can specify that an attribute or element value is a space-separated list of integers.  
  
 For comprehensive information about deriving new simple types by using the list mechanism, refer to the W3C Web site. For various links to this and other Web sites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 To derive a simple type as a list of that type, select the relevant **Field Element** node or **Field Attribute** node in the schema tree and then, in the Properties window, select a simple type from the drop-down list for the **Base Data Type** property. As soon as you select a value for this property, the **Derived By** property automatically changes from its default value to **Restriction**, which serves as the default value for type derivation. You must change the **Derived By** property from **Restriction** to **List**, which causes the **Base Data Type** property to be renamed as the **Item Type** property (incidentally, the renamed property moves to a different position in the property list due to the alphabetical sorting of the properties).  
  
> [!NOTE]
>  You can use the restriction and list mechanisms together, creating a named simple type derivation by using the restriction mechanism, and then using that as the item type in another simple type derivation by using the list mechanism. This can result, for example, in a value that is constrained to be a list of space-separated strings belonging to a particular enumerated set of strings.  
  
> [!CAUTION]
>  Using the list mechanism for simple type derivation can be complicated when the item type you choose is one that itself allows spaces, such as strings. This is because the list mechanism uses spaces to separate values of the allowed type in the list.  
  
 When you first change a **Field Element** node or **Field Attribute** node from having a data type to having a base data type (thereby starting the process of simple type derivation), and then set the **Derived By** property to **List**, you can observe the following change in the corresponding fragment in the XSD view:  
  
-   Before, with a newly inserted **Field Element** node named **ZipCodeList**.  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="ZipCodeList" type="xs:string" />  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
-   After setting the **Base Data Type** property to xs:integer, and setting the **Derived By** property to **List** (after which the **Base Data Type** property is renamed to be the **Item Type** property).  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="ZipCodeList">  
                    <xs:simpleType>  
               <xs:list itemType="xs:integer" />   
                       </xs:simpleType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
> [!NOTE]
>  In a real-life schema, it would be better to first define and name a simple type derivation of integer that restricts the integer to five digits, and then to derive the **ZipCodeList** element from that type, effectively limiting the list to integers having five digits.  
  
## See Also  
 [Simple Type Derivation](../core/simple-type-derivation.md)
