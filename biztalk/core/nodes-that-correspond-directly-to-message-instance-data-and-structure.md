---
title: "Nodes That Correspond Directly to Message Instance Data and Structure | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18cf721c-2972-43c6-8ae4-f2f8f83ba2c5
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Nodes That Correspond Directly to Message Instance Data and Structure
Some of the node types that you use to create schemas in BizTalk Editor correspond directly to elements and attributes in XML representation of instance messages governed by the schema (for other instance message formats, such as flat file formats, this correspondence only exists after translation from the other format and before translation to the other format). These node types are **Record** nodes (including root **Record** nodes), **Field Element** nodes, and **Field Attribute** nodes.  
  
 The values you give to the **Node Name** property of **Record** and **Field Element** nodes specify the name of the corresponding element in XML instance messages governed by the schema. Likewise, the values you give to the **Node Name** property of **Field Attribute** nodes specify the name of the corresponding attribute in XML instance messages governed by the schema. More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 The remainder of this section provides more information about this class of nodes, with root **Record** nodes receiving separate treatment due to their special role in schemas.  
  
## Next steps 
  
-   [Root Nodes](../core/root-nodes.md)  
  
-   [Record Nodes](../core/record-nodes.md)  
  
-   [Field Element Nodes](../core/field-element-nodes.md)  
  
-   [Field Attribute Nodes](../core/field-attribute-nodes.md)