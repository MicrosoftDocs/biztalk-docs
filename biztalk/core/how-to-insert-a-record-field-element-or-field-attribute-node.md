---
description: "Learn more about: How to Insert a Record, Field Element, or Field Attribute Node"
title: "How to Insert a Record, Field Element, or Field Attribute Node"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Insert a Record, Field Element, or Field Attribute Node
**Record** nodes (including the **Root** node), **Field Attribute** nodes, and **Field Element** nodes are unique in that they can be renamed so that their names represent the names of the actual, custom-named elements in a corresponding instance message. For example, if you name a **Record** node FullName, at the corresponding location in an instance message an XML element named FullName is expected. If that **Record** node named FullName has a child **Field Attribute** node named RequireFullMiddleName (with its **Min Occurs** and **Max Occurs** properties set to **1**), the **FullName** element in a corresponding instance message will need to have an attribute named **RequireFullMiddleName** associated with it.  
  
 All **Record** nodes, when initially inserted, are represented in the XSD as with a **complexType** element, but not with a subsequent **sequence**, **choice**, or **all** element. For this reason, the **Group Order Type**, **Group Max Occurs**, and **Group Min Occurs** properties of the **Record** node are not available for modification.  
  
 As soon as you add a child **Record** or **Field Element** node to the **Record** node, a **sequence** element is added to the XSD representation within the **complexType** element to contain this first child node, and the **Group Order Type** property of the **Record** node shows a value of **Sequence**. In most circumstances, you can change the **Group Order Type** property from **Sequence** to **Choice**, and in more limited circumstances, from **Sequence** to **All**, thereby changing the element pair that contains the corresponding child nodes to either **complexType/choice** or **complexType/all**, respectively.  
  
 **Field Attribute** nodes cannot have the same node names while in the same scope.  
  
 **Record** and **Field Element** nodes can have the same node names while in the same scope only if the following conditions are met:  
  
-   They have the same data type.  
  
-   They are not within an **All Group** node.  
  
### To insert a new child Record node, Field Element node, or Field Attribute node within the Schema node or an existing Record node  
  
1.  Select the **Schema** node or an existing **Record** node.  
  
2.  On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Child Record**, **Child Field Element**, or **Child Field Attribute**, as appropriate.  
  
    > [!NOTE]
    >  A child node of the chosen type is added after either the last node in the schema tree (when inserting within the **Schema** node) or after the last existing child node of the selected **Record** node (when inserting within an existing **Record** node).  
  
3.  Type a name for the newly inserted **Record**, **Field Element**, or **Field Attribute** node, and then press ENTER.  
  
### To insert a sibling Record node, Field Attribute node, or Field Element node within an existing Record node  
  
1.  Select any child node of the **Record** node into which you want to insert the sibling **Record**, **Field Attribute**, or **Field Element** node.  
  
2.  On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Sibling Record**, **Sibling Field Attribute**, or **Sibling Field Element**, as appropriate.  
  
     A sibling node of the chosen type is inserted at the end of the siblings of the selected node.  
  
3.  Type a name for the newly inserted **Record**, **Field Attribute**, or **Field Element** node, and then press ENTER.  
  
## See Also  
 [Inserting Nodes into a Schema](../core/inserting-nodes-into-a-schema.md)
