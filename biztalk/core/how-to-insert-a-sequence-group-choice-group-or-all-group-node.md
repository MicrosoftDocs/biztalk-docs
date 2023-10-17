---
description: "Learn more about: How to Insert a Sequence Group, Choice Group, or All Group Node"
title: "How to Insert a Sequence Group, Choice Group, or All Group Node"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Insert a Sequence Group, Choice Group, or All Group Node
BizTalk Editor supports three types of group nodes for elements: **Sequence Group**, **Choice Group**, and **All Group**. These different types of group nodes establish different constraints on the child nodes of the group in corresponding instance messages. For information about the constraints of these different types of groups, you should refer directly to information about the XML Schema definition (XSD) language on the Web. For links to this information, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 BizTalk Editor also supports a group node for attributes, the **Attribute Group** node. This type of node allows a set of attributes to be defined once, and then be associated with more than one **Record** node within the schema.  
  
 When you build structure into your schema, **Record** nodes are assumed to contain ordered sequences of child nodes by default, and are represented by using **sequence** elements in the XSD representation of the schema. You can change the type of a group node by changing its **Order Type** property.  
  
### To insert a Sequence Group node or a Choice Group node  
  
1.  In the schema tree view, select the **Record** node in which you want to insert the **Sequence Group** node or the **Choice Group** node.  
  
2.  On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Sequence Group** or **Choice Group**, as appropriate.  
  
### To insert an All Group node  
  
1.  In the schema tree view, select the new **Record** node in which you want to insert the **All Group** node.  
  
2.  On the **BizTalk** menu, point to **Insert Schema Node**, and then click **All Group**.  
  
> [!NOTE]
>  The **All Group** choice is only available on the BizTalk (or shortcut) menu when the relevant parent **Record** node meets the constraints that XSD imposes on the use of the **all** element.  
  
> [!NOTE]
>  The **All Group** choice requires that the **Record** node have a base data type. A quick way to give the node a data type is to set its **Content Type** to **Complex**.  
  
### To insert an Attribute Group node  
  
1.  In the schema tree view, select the **Record** node in which you want to insert the **Attribute Group** node.  
  
2.  On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Attribute Group**.  
  
> [!NOTE]
>  If you want to change the name of the newly inserted **Attribute Group** node, type the new name in its **Group Reference** property.  
  
## See Also  
 [Inserting Nodes into a Schema](../core/inserting-nodes-into-a-schema.md)
