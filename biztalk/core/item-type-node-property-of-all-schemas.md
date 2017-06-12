---
title: "Item Type (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Item Type property [schemas]"
ms.assetid: ba4cb81e-8427-4b22-9157-d84d75852c10
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Item Type (Node Property of All Schemas)
Use the **Item Type** property to specify the data type that corresponds to a **Derived By** property setting of **List**.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
 Any of the simple types in the drop-down list, which you may type or choose from the list.  
  
## Default Value  
 xs:string  
  
## XSD Persistence  
 As the value of the **itemType** attribute of the **simpleType/list** elements within the **element** or **attribute** element that corresponds to the selected **Field Element** or **Field Attribute** node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **List**.  
  
 Use this property to specify the data type of the items in the list. Typical settings are a list of strings, a list of integers, and so on. For example, to allow the following type of values for the **PONumbers** element in an instance message, you could define a **Field Element** node with its **Derived By** property set to **List** and its **Item Type** property set to **xs:integer**:  
  
```  
<PONumbers>100 101 2002 400</PONumbers>  
  
```  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)