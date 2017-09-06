---
title: "Nodes That Control Instance Message Structure and Variations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3af8e6ce-282d-4318-a538-046b423ef033
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Nodes That Control Instance Message Structure and Variations
Some of the node types that you use to create schemas in BizTalk Editor control the structure of, and variations within, instance messages. You use **Sequence Group** nodes to specify that a sequence of elements must occur in a specific order in the corresponding location in an instance message. You use **Choice Group** nodes to specify that one element from a collection of elements can occur in the corresponding location in an instance message. You use **All Group** nodes to specify that all of the specified elements can occur in any order, but only once, at the corresponding location in an instance message. **\<Equivalent>** nodes and their child nodes are displayed in the schema tree to indicate locations in instance messages where derivation-based polymorphism is in effect, allowing one of many related complex data types to occur in the corresponding location in an instance message.  
  
 The remainder of this section provides additional information about this class of nodes.  
  
## In This Section  
  
-   [Sequence Group Nodes](../core/sequence-group-nodes.md)  
  
-   [Choice Group Nodes](../core/choice-group-nodes.md)  
  
-   [All Group Nodes](../core/all-group-nodes.md)  
  
-   [\<Equivalent> Nodes and Their Child Nodes](../core/equivalent-nodes-and-their-child-nodes.md)