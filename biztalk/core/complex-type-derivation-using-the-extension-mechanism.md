---
title: "Complex Type Derivation Using the Extension Mechanism | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7125fb5b-f77a-47c9-8000-f2332940df89
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Complex Type Derivation Using the Extension Mechanism
A complex type derived by extension is a functional superset of its base data type. As the name implies, its base data type is the basis for the type being defined, where the differences from the base type are additive. This topic provides an example in which the two elements **ShippingAddress** and **BillingAddress** are based on the complex global type **GlobalAddrType**. **ShippingAddress** is simply defined to be of type **GlobalAddrType**, whereas **BillingAddress** is defined to extend the type **GlobalAddrType**. At the end of the example, an additional element is added to **BillingAddress**, named **Department**, with a type of string and a default value of Accounts Payable.  
  
 For comprehensive information about deriving new complex types by using the extension mechanism, refer to the W3C website. For various links to this and other websites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 To derive from a complex global type by extension, in another location in the schema tree, begin by inserting a new **Record** node at the desired location. Then set its **Base Data Type** property to the name of a complex global type.  
  
 In the following example, **BillingAddress** is the name of the newly inserted **Record** node, and **GlobalAddrType** is the name of the complex global type from which it derives, and intends to extend. In the schema tree view, after **Base Data Type** has been set to **GlobalAddrType**, a duplicate node structure would be displayed below the node named **BillingAddress**, identical to the adjacent node structure under the node named **ShippingAddress**. The difference between them is that the **BillingAddress** node structure will be extensible beyond the base data type **GlobalAddrType**, and the **ShippingAddress** structure will remain identical to the base data type **GlobalAddrType**.  
  
- Before, with a newly inserted node named **BillingAddress**.  
  
  ```  
  <xs:schema>  
      <xs:element name="Root">  
          <xs:complexType>  
              <xs:sequence>  
                  <xs:element name="ShippingAddress" type="GlobalAddrType" />  
                  <xs:element name="BillingAddress">  
                      <xs:sequence />  
                  </xs:element>  
              </xs:sequence>  
          </xs:complexType>  
      </xs:element>  
      <xs:complexType name="GlobalAddrType">  
      [Address structure defined globally here.]  
      </xs:complexType>  
  </xs:schema>  
  ```  
  
- After deriving from the complex base type **GlobalAddrType**, by extension.  
  
  ```  
  <xs:schema>  
      <xs:element name="Root">  
          <xs:complexType>  
              <xs:sequence>  
                  <xs:element name="ShippingAddress" type="GlobalAddrType" />  
                  <xs:element name="BillingAddress">  
                      <xs:complexType>  
                          <xs:complexContent mixed="false">  
                              <xs:extension base="GlobalAddrType" />  
                          </xs:complexContent>  
                      </xs:complexType>  
                  </xs:element>  
              </xs:sequence>  
          </xs:complexType>  
      </xs:element>  
      <xs:complexType name="GlobalAddrType">  
      [Address structure defined globally here.]   
      </xs:complexType>  
  </xs:schema>  
  ```  
  
  You specify extensions to the base data type by inserting nodes into the **BillingAddress** node in the schema tree. The following XSD fragment shows how the empty extension element is expanded when a **Sequence Group** node is inserted as a new child of the **BillingAddress** node and then a **Field Element** node, named **PaymentType**, is inserted as a child node of the **Sequence Group** node.  
  
```  
<xs:extension base="GlobalAddrType">  
    <xs:sequence>  
        <xs:element default="Accounts Payable"  
            name="Department" type="xs:string" />  
    </xs:sequence>  
</xs:extension>  
```  
  
## See Also  
 [Complex Global Type Derivation](../core/complex-global-type-derivation.md)