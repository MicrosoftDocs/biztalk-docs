---
title: "Derived By (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Derived By property [schemas]"
ms.assetid: d9b89527-6611-4cc6-af58-e2e6334f8b0d
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Derived By (Node Property of All Schemas)
Use the **Derived By** property to define whether the data type being derived for the currently selected **Record**, **Field Element**, or **Field Attribute** node is an extension, restriction, list, or union of the type specified by the **Base Data Type** property.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
 The following table shows the choices for this property when a **Record** node is selected.  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Use this value to return to the default behavior: the data type of the selected **Record** node is not derived from another type.|  
|**Extension**|Use this value to derive a new, extended data type from the simple or complex data type defined by the [Content Type](../core/content-type-node-property-of-all-schemas.md) and [Base Data Type](../core/base-data-type-node-property-of-all-schemas.md) properties.|  
|**Restriction**|Use this value to derive a new, restricted data type from the simple or complex data type defined by the **Content Type** and **Base Data Type** properties.|  
  
 The following table shows the choices for this property when a **Field Element** or **Field Attribute** node is selected.  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**(Default)**|Use this value to return to the default behavior: the data type of the selected **Field Element** or **Field Attribute** node is not derived from another type.|  
|**Restriction**|Use this value to derive a new, restricted data type from the simple data type defined by the **Content Type** and **Base Data Type** properties.<br /><br /> When you specify this value, all of the properties in the **Restricted** category become available for contriving a specific set of data restrictions.|  
|**List**|Use this value to specify that instance message data that corresponds to the selected **Field Element** or **Field Attribute** node can be a list of white-space separated values of the data type specified by the [Item Type](../core/item-type-node-property-of-all-schemas.md) property.<br /><br /> Use caution when the **Base Data Type** property specifies "xs:string" because strings can themselves contain white space which introduces ambiguity into the data.|  
|**Union**|Use this value to specify that the instance message data that corresponds to the selected **Field Element** or **Field Attribute** node can be one of several different data types, as specified by the [Member Types](../core/member-types-node-property-of-all-schemas.md) property.|  
  
## Default Value  
 **(Default)**, indicating that the data type of the currently selected **Record**, **Field Element**, or **Field Attribute** node is not derived from another data type.  
  
## XSD Persistence  
 The XSD persistence of the **Derived By**, **Base Data Type**, **Content Type** (**Record** nodes only), **Item Type**, and **Member Types** properties are interrelated, as shown in the following table.  
  
|Node type and property settings|XSD persistence|  
|-------------------------------------|---------------------|  
|**Record** node with:<br /><br /> **Derived By** = **Extension**<br /><br /> **Content Type** = **SimpleContent**|\<element><br /><br /> \<complexType><br /><br /> \<simpleContent><br /><br /> \<extension base="*BDT*"><br /><br /> where "*BDT*" is the value of the **Base Data Type** property.|  
|**Record** node with:<br /><br /> **Derived By** = **Extension**<br /><br /> **Content Type** = **ComplexContent**|\<element><br /><br /> \<complexType><br /><br /> \<complexContent><br /><br /> <extension base="\<*Base Data Type*>"|  
|**Record** node with:<br /><br /> **Derived By** = **Restriction**<br /><br /> **Content Type** = **SimpleContent**|\<element><br /><br /> \<complexType><br /><br /> \<simpleContent><br /><br /> restriction base="*BDT*"><br /><br /> where "*BDT*" is the value of the **Base Data Type** property.|  
|**Record** node with:<br /><br /> **Derived By** = **Restriction**<br /><br /> **Content Type** = **ComplexContent**|\<element><br /><br /> \<complexType><br /><br /> \<complexContent><br /><br /> \<restriction base="*BDT*"><br /><br /> where "*BDT*" is the value of the **Base Data Type** property.|  
|**Field Element** or **Field Attribute** node with:<br /><br /> **Derived By** = **Restriction**|\<element> or \<attribute>, respectively<br /><br /> \<simpleType><br /><br /> \<restriction base="*BDT*"><br /><br /> where "*BDT*" is the value of the **Base Data Type** property.|  
|**Field Element** or **Field Attribute** node with:<br /><br /> **Derived By** = **List**|\<element> or \<attribute>, respectively<br /><br /> \<simpleType><br /><br /> \<list itemType="*IT*"><br /><br /> where "*IT*" is the value of the **Item Type** property.|  
|**Field Element** or **Field Attribute** node with:<br /><br /> **Derived By** = **Union**|\<element> or \<attribute>, respectively<br /><br /> \<simpleType><br /><br /> \<union memberTypes="*MTs*"><br /><br /> where "*MTs*" is the value of the **Member Types** property.|  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** (including a root **Record** node), **Field Element**, or **Field Attribute** node in BizTalk Editor.  
  
 The setting of this property interacts with the **Base Data Type**, **Content Type** (**Record** nodes only), **Item Type**, and **Member Types** properties.  
  
 For **Field Element** and **Field Attribute** nodes (not for **Record** nodes), if you set the **Derived By** property to **Restriction**, the following properties, which represent **simpleType** facets in XSD, become available for you to edit:  
  
-   [Enumeration](../core/enumeration-node-property-of-all-schemas.md)  
  
-   [Length](../core/length-node-property-of-all-schemas.md)  
  
-   [MaxFacet Type](../core/maxfacet-type-node-property-of-all-schemas.md)  
  
-   [MaxFacet Value](../core/maxfacet-value-node-property-of-all-schemas.md)  
  
-   [Maximum Length](../core/maximum-length-node-property-of-all-schemas.md)  
  
-   [MinFacet Type](../core/minfacet-type-node-property-of-all-schemas.md)  
  
-   [MinFacet Value](../core/minfacet-value-node-property-of-all-schemas.md)  
  
-   [Minimum Length](../core/minimum-length-node-property-of-all-schemas.md)  
  
-   [Pattern](../core/pattern-node-property-of-all-schemas.md)  
  
 When you change the value of the [Derived By (Node Property of All Schemas) &#91;BTS05&#93;](../core/derived-by-node-property-of-all-schemas.md) property, any value associated with the [Fixed](../core/fixed-node-property-of-all-schemas.md) or the [Default Value](../core/default-value-node-property-of-all-schemas.md) property is deleted (they cannot both have a value). As appropriate, you must provide a new value for the **Fixed** or **Default Value** property that conforms to the chosen **Base Data Type** and (new) **Derived By** property settings.  
  
 Moreover, you cannot set the **Derived By** property to **Extension** to derive from *xs:anyType* otherwise you may receive an error message as in the below Note section. To correct this error, you can either change **Derived By** property to **Restriction** or change the **Base Data Type** from *xs:anyType* to some other type.  
  
> [!NOTE]
>  Wildcard '##any' allows element 'ACTUAL_FIELD_NAME', and causes the content model to become ambiguous. A content model must be formed such that during validation of an element information item sequence, the particle contained directly, indirectly or implicitly therein with which to attempt to validate each item in the sequence in turn can be uniquely determined without examining the content or attributes of that item, and without any information about the items in the remainder of the sequence.  
  
 For more information about different types of derivations, see [Type Reuse and Derivations](../core/type-reuse-and-derivations.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)