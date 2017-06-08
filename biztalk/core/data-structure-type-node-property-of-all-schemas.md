---
title: "Data Structure Type (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Data Structure Type property [schemas]"
ms.assetid: 2a581300-66c3-4bc6-906b-fd1c58dc5ab9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Structure Type (Node Property of All Schemas)
Use the **Data Structure Type** property to:  
  
-   Select an existing global complex type to be associated with the selected **Record** node, thereby converting the inbuilt complex type for this **Record** node to a global complex type.  
  
     \- or -  
  
-   Specify a name for the complex type associated with the selected **Record** node, thereby converting its unnamed complex type to a global complex type, or,  
  
     \- or -  
  
-   Reference an existing global **Record** node.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 General  
  
## Allowed Values  
 Valid qualified names (QNames).  
  
## Default Value  
 None.  
  
## XSD Persistence  
 When you choose an existing complex type, or type a new complex type name for this property, it is persisted as the value of **type** attribute of the element that corresponds to the selected **Record** node.  
  
 When you choose to refer to an existing global Record node, this property value is persisted as the value of the **ref** attribute of the element that corresponds to the selected **Record** node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 If the value of this property is blank, the complex type of the underlying **Record** node is unnamed, and therefore cannot be used by any other **Record** node. If you type a new name for this property, the underlying complex type becomes global and can be used as the value of the **Data Structure Type** or **Base Data Type** property of other **Record** nodes. You can also select a value from a list of existing global named complex types using the drop-down list, or type a name of an existing complex type to reuse that type.  
  
 Further, you can also use this property to reference an existing global **Record** node by choosing it from the drop-down list.  
  
 In summary, the drop-down list for this property has two types of entries in it:  
  
-   Existing global named complex types  
  
-   Existing global Record nodes  
  
 And because the property field is editable, you can provide a name for an already present, unnamed complex type.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)