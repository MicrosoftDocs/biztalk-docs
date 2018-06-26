---
title: "Property Interdependencies | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ed5b75e-db1c-43d4-a287-fc4cd1c529f5
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Property Interdependencies

## Overview
As you use BizTalk Editor, and specifically the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, to change the values of properties, you will notice that there are extensive interdependencies between properties. Sometimes a particular setting for one property will cause other properties to be automatically cleared, become enabled or disabled, or even appear or disappear entirely from the Properties window. These interdependencies are too numerous to cover. 

However, the following list provides some common examples to give you an idea of how they work:  
  
- When setting the properties of a **Field Element** node or **Field Attribute** node for which a data type is being derived from a simple type by using the restriction mechanism, an entire new category of properties becomes available: **Restriction**. Further, the properties in this new category are enabled or disabled based on whether the base data type is of a string type or a numeric type. For more information about this form of simple type derivation, see [Simple Type Derivation Using the Restriction Mechanism](../core/simple-type-derivation-using-the-restriction-mechanism.md).  
  
- When setting the properties of a **Field Element** node or **Field Attribute** node for which a data type is being derived from a simple type by using either the list or union mechanism, the **Base Data Type** property is changed to either the **Item Type** property or the **Member Types** property, respectively. In the latter case, the corresponding drop-down list is modified to include check boxes, allowing multiple types to be selected. For more information about these forms of simple type derivation, see [Simple Type Derivation Using the List Mechanism](../core/simple-type-derivation-using-the-list-mechanism.md) and [Simple Type Derivation Using the Union Mechanism](../core/simple-type-derivation-using-the-union-mechanism.md).  
  
- To expose the properties associated with flat file schemas, you must set the **Schema Editor Extensions** property of the **Schema** node to include the **Flat File Extension**. The custom properties associated with other editor extensions, such as the EDI extension, are exposed in the same way: by choosing the corresponding extension using the **Schema Editor Extensions** property.  
  
  This list includes examples that are meant to illustrate the types of property interdependencies that you will see when working within the Properties window, but it is not meant to be an exhaustive list of such interdependencies.  
  
## See Also  
- [Node Properties](../core/node-properties.md)   
- The following properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
   -  Node Properties Alphabetical Listings
   -  Node Properties of All Schemas 
   -  Schema Editor Extensions