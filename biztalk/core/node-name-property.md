---
title: "Node Name Property | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95d9e5bf-7439-4ef4-ad14-e8d3e8eff911
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Node Name Property
As you use BizTalk Editor to insert nodes into the schema tree, some nodes are meant to be renamed and others are not. Essentially, you can and should rename **Record** nodes, **Field Element** nodes, and **Field Attribute** nodes. The names that you give to these nodes will become the names of the XML elements and attributes in the message that the schema defines.  
  
 In the schema tree, the nodes that you cannot rename are shown in the form of XML tags; that is, with the less than (\<) and greater than (>) signs. For example, the **Schema** node, **Choice Group** nodes, **Any Element** nodes, and **Any Attribute** nodes are represented in the schema tree with the names \<Schema>, \<Choice>, \<Any>, and \<AnyAttribute>, respectively. The **Node Name** property for such nodes is read-only.  
  
 Within a given **Record** node, you cannot have two **Field Attribute** nodes with the same name. However, you can have more than one **Field Element** node or **Record** node with the same name as child nodes of the same **Record** node, as long as they all have the same data type (as specified by their **Data Type** property for **Field Element** nodes or their **Data Structure Type** for **Record** nodes).  
  
 When you give names to **Record** nodes, **Field Element** nodes, and **Field Attribute** nodes, use names that are descriptive of the role of that element or attribute within the message being defined by the schema. For example, FirstName is probably a good choice for the name of a **Field Element** node that will be used to store the first name of someone in an address structure. In an XML instance message where the first name James occurs, the corresponding element would look like the following.  
  
```  
    <FirstName>James</FirstName>  
```  
  
 When you are renaming **Record** nodes, **Field Element** nodes, and **Field Attribute** nodes, you should be aware that not all characters are allowed in node names. For information about these disallowed characters, see [Which Node Name Characters Get Encoded](../core/which-node-name-characters-get-encoded.md). Although BizTalk Editor allows you to use disallowed characters by encoding them, it is often simpler to avoid such characters altogether. For information about how disallowed characters are encoded, see [How Node Name Characters Get Encoded](../core/how-node-name-characters-get-encoded.md).  
  
 In addition to the characters that are disallowed in node names, unless they are encoded in the XSD representation of the schema, you should not use C# reserved words as the names of any root nodes in the schema tree (unless you provide a valid **RootNode TypeName** property value) or as schema file names.  
  
## In This Section  
  
-   [Which Node Name Characters Get Encoded](../core/which-node-name-characters-get-encoded.md)  
  
-   [How Node Name Characters Get Encoded](../core/how-node-name-characters-get-encoded.md)