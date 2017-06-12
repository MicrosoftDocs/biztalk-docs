---
title: "Group Order Type (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Group Order Type property [schemas]"
ms.assetid: 9f495e5b-6552-48e3-8995-984d9757308d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Group Order Type (Node Property of All Schemas)
Use the **Group Order Type** property to specify the type of group ordering of child nodes below the selected **Record** node.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**All**|Specifies the element group as an all group. All groups allow their child elements to appear zero (0) or one (1) time, and in any order, in instance messages. Restrictions apply; see remarks for more information. **Note:**  You can use **All Group** nodes only in relation to inheritance; they cannot generally be inserted directly into a schema. See remarks for additional information.|  
|**Choice**|Specifies the element group as a choice group. A choice group allows only one of its child elements to appear in instance messages.|  
|**Sequence**|Specifies the element group as a sequence group. Sequence groups require that child elements in instance messages appear in the same order as defined in the schema. This is the default value.|  
  
## Default Value  
 **Sequence**  
  
## XSD Persistence  
 As a **sequence**, **choice**, or **all** element within the element that corresponds to the selected **Record** node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor.  
  
 This value for this property controls the type of group that is persisted and meets the XSD requirement for having a group at every complex structure definition point. Use the **Group Order Type** property to modify group types. The group will be created automatically when the first child node is inserted.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 The **All Group** node has a number of special restrictions to which the **Sequence Group** and **Choice Group** nodes are not subject:  
  
-   All groups may not have any child groups.  
  
-   Every child of an all group must be an individual element.  
  
-   No element under this group node may appear more than once.  
  
-   To avoid ambiguity in instance messages, the all group must be the first element group within its containing **Record** node.  
  
 Whenever you insert a **Record** node and start inserting nodes within it, a hidden sequence group is always created by default immediately under that **Record** node. This default group order type can be changed using the **Group Order Type** property of the **Record** node. Because an **All Group** node cannot occur within any other group node, and the use of a hidden sequence group, you cannot insert an **All Group** node within a **Record** node in BizTalk Editor.  
  
 However, there is one exceptional case in which you can directly insert an **All Group** node and directly modify its properties. When complex type inheritance is used in a schema, BizTalk Editor exposes the top-level group node, and therefore allows insertion, deletion, and modification of an **All Group** node.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)