---
title: "Min Occurs (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Min Occurs property [schemas]"
  - "Min Occurs property [schemas], about Min Occurs property"
ms.assetid: f9676bf6-3a90-4d7f-822e-47c28cf31717
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Min Occurs (Node Property of All Schemas)
Use the **Min Occurs** property to specify the minimum number of times that the element(s) corresponding to the selected node can occur in a given scope in an instance message.  
  
> [!NOTE]
>  If an ancestor node can occur multiple times, the total occurrences of the selected node can be greater than the occurrence range specified by the values of this property and the [Max Occurs](../core/max-occurs-node-property-of-all-schemas.md) property.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md), [Sequence Group](../core/sequence-group-node-properties.md), [Choice Group](../core/choice-group-node-properties.md), [All Group](../core/all-group-node-properties.md), [Any Element](../core/any-element-node-properties.md)  
  
## Category  
 General  
  
## Allowed Values  
  
|Edit box value|Description|  
|--------------------|-----------------|  
|Positive integer|Any value greater than or equal to one (1) will require the corresponding element(s) in an instance message to occur at least that many times. The value of this property must be less than the value set for the [Max Occurs](../core/max-occurs-node-property-of-all-schemas.md) property of the same ndoe.|  
|Zero (0)|Use this value if the element(s) corresponding to the selected node need not even occur once in instance messages.|  
|No value|Use this property value to restore the behavior to the default value of one (1).|  
  
## Default Value  
 No value, resulting in the default behavior corresponding to a value of one (1).  
  
## XSD Persistence  
 As the value of the **minOccurs** attribute of the element that corresponds to the selected node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select node of an appropriate type, including root **Record** nodes, in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 Any value set for this property must be less than or equal to the value specified for the **Max Occurs** property.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)