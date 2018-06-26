---
title: "BizTalk Representation of Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0460a37-1f4f-4c0b-91db-bb457f434fe9
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Representation of Schemas

## Overview
Although BizTalk schemas are ultimately represented and persisted in the XML Schema definition (XSD) language, they are represented as a graphical hierarchy of nodes when working in BizTalk Editor. The top of the hierarchy is always the **\<Schema\>** node, and the remaining types of nodes are used to build the schema so that it represents a particular message that is exchanged by using BizTalk.  

## Insert schema node options  
 BizTalk Editor provides a way to construct XSD schemas without needing to learn all of the intricacies of XSD syntax. When using the **Insert Schema Node** command on the **BizTalk** menu or the shortcut menu, the following choices for nodes to be inserted are available on the cascading menu.  


| Insert Schema Node menu choice |                                                                                                                                                                                                                                          Description                                                                                                                                                                                                                                          |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **Child Record**        |                                                                                                                                                           Inserts a **Record** node at the end of the sequence within the selected node. For more information about **Record** nodes, see [Record Nodes](../core/record-nodes.md).                                                                                                                                                            |
|   **Child Field Attribute**    |                                                                                                                                  Inserts a **Field Attribute** node at the end of the selected **Record** or **Attribute Group** node. For more information about **Field Attribute** nodes, see [Field Attribute Nodes](../core/field-attribute-nodes.md).                                                                                                                                   |
|    **Child Field Element**     |                                                                                                                                                           Inserts a **Field Element** node within the selected node. For more information about **Field Element** nodes, see [Field Element Nodes](../core/field-element-nodes.md).                                                                                                                                                           |
|       **Sibling Record**       |                                                                                                                                                         Inserts a **Record** node at the end of the sequence containing the selected node. For more information about **Record** nodes, see [Record Nodes](../core/record-nodes.md).                                                                                                                                                          |
|  **Sibling Field Attribute**   |                                                                                                                        Inserts a **Field Attribute** node at the end of the **Record** or **Attribute Group** node containing the selected node. For more information about **Field Attribute** nodes, see [Field Attribute Nodes](../core/field-attribute-nodes.md).                                                                                                                         |
|   **Sibling Field Element**    |                                                                                                                                           Inserts a **Field Element** node at the end of the sequence containing the selected node. For more information about **Field Element** nodes, see [Field Element Nodes](../core/field-element-nodes.md).                                                                                                                                            |
|       **Sequence Group**       |                                                                                                                           Inserts a **Sequence Group** node (\<Sequence\> in the tree view) at the end of the sequence within the selected node. For more information about **Sequence Group** nodes, see [Sequence Group Nodes](../core/sequence-group-nodes.md).                                                                                                                            |
|        **Choice Group**        |                                                                                                                                Inserts a **Choice Group** node (\<Choice\> in the tree view) at the end of the sequence within the selected node. For more information about **Choice Group** nodes, see [Choice Group Nodes](../core/choice-group-nodes.md).                                                                                                                                 |
|         **All Group**          | Inserts an **All Group** node (\<All\> in the tree view) as the only non-attribute child node of a **Record** node, replacing the default use of a **sequence** element within the **Record** node with the use of an **all** element. Before you can insert an **All Group** node, you must change the **Content Type** property of the containing **Record** node to **ComplexContent**. For more information about **All Group** nodes, see [All Group Nodes](../core/all-group-nodes.md). |
|      **Attribute Group**       |                                                                                  Inserts an **Attribute Group** node (\<AttrGroup:attrGroup*N*\> in the tree view, where *N* is a monotonically increasing numeral) at the end of the selected **Record** or **Attribute Group** node. For more information about **Attribute Group** nodes, see [Attribute Group Nodes](../core/attribute-group-nodes.md).                                                                                   |
|        **Any Element**         |                                                                                 Inserts an **Any Element** node (<strong>\<</strong>Any<strong>\></strong> in the tree view) at the end of the sequence within the selected **Record**, **Sequence Group**, **Choice Group**, or **All Group** node. For more information about **Any Element** nodes, see [Any Element Nodes](../core/any-element-nodes.md).                                                                                 |
|       **Any Attribute**        |                                                                                         Inserts an **Any Attribute** node (<strong>\<</strong>AnyAttribute<strong>\></strong> in the tree view) at the end of the sequence within the selected **Record** or **Attribute Group** node. For more information about **Any Attribute** nodes, see [Any Attribute Nodes](../core/any-attribute-nodes.md).                                                                                         |

 In many cases, adding a single node in BizTalk Editor results in the addition of multiple nested elements within the corresponding XSD representation of the schema. Because these nested elements can have complex syntax, using BizTalk Editor to graphically arrange nodes is a much less error-prone approach to constructing XSD schemas than hand-editing the XSD. Another factor to consider is that always using BizTalk Editor to construct XSD schemas results in a more controlled subset of XSD being used in the schema descriptions.  

 Overall, BizTalk Editor combines a simplified approach to constructing XSD schemas using the generic concepts of Records and Fields with a more explicit control of particular XSD constructs, such as **sequence**, **choice**, **any**, and **anyattribute** elements.  

 Each type of node has a unique set of properties that can be configured in the Visual Studio Properties window. In general, these properties correspond to attributes on the XSD elements in the corresponding XSD representation of the schema. For more information about node properties, see **Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

 This section describes the types of nodes used within BizTalk Editor, briefly discusses their properties, and provides links to reference information about their properties.  

## Next steps

-   [Nodes That Correspond Directly to Message Instance Data and Structure](../core/nodes-that-correspond-directly-to-message-instance-data-and-structure.md)  

-   [Nodes That Control Instance Message Structure and Variations](../core/nodes-that-control-instance-message-structure-and-variations.md)  

-   [Nodes That Simplify Schema Creation](../core/nodes-that-simplify-schema-creation.md)  

-   [Nodes That Provide Wildcard Capabilities](../core/nodes-that-provide-wildcard-capabilities.md)  

-   [Node Properties](../core/node-properties.md)