---
title: "How to Set the Source Links Compiler Value | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4edd1d73-78d1-468d-806a-3f6f258ee375
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set the Source Links Compiler Value
You can use the **Source Links** property of a link to specify how a value is retrieved from the source node and applied to the destination node. This topic explains the available choices and how to choose among them.  
  
### To set the Source Links link property  
  
1. In BizTalk Mapper, in a grid page, click a link to select it.  
  
    The endpoints of a selected link in the grid page are highlighted.  
  
2. In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, set the **Source Links** property to one of the following choices:  
  
   -   **Copy Name.** The name of the node in the source schema is used as the value of the linked node in the destination schema.  
  
   -   **Copy Text Value.** The value corresponding to the node in the source schema (element data or an attribute value) is used as the value of the linked node in the destination schema. This choice is the default. For example, `<Node>Hello<Name>Chris</Name>Barry</Node>` would result in "Hello".  
  
   -   **Copy Text and Subcontent Value.** The value corresponding to the record node, and the value of all its child nodes, and their child nodes, in the source schema (element data and attribute values) are combined as the value of the linked node in the destination schema. For example, `<Node>Hello<Name>Chris</Name>Barry</Node>` would result in "Hello Chris Barry".  
  
## See Also  
 [Using Links to Specify Record and Field Mappings](../core/using-links-to-specify-record-and-field-mappings.md)   
 [Compiler Directives and Links](../core/compiler-directives-and-links.md)