---
title: "Max Occurs (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Max Occurs property [schemas]"
  - "Max Occurs property [schemas], about Max Occurs property"
ms.assetid: 0ecf0ff2-26c3-4420-951c-a09f763b7c3d
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Max Occurs (Node Property of All Schemas)
Use the **Max Occurs** property to configure the maximum number of times that the element or elements corresponding to the selected node can occur in a given scope in an instance message.  
  
> [!NOTE]
>  If an ancestor node can occur multiple times, the total occurrences of the selected node can be greater than the occurrence range specified by the values of the [Min Occurs](../core/min-occurs-node-property-of-all-schemas.md) property and this property.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md), [Sequence Group](../core/sequence-group-node-properties.md), [Choice Group](../core/choice-group-node-properties.md), [All Group](../core/all-group-node-properties.md), [Any Element](../core/any-element-node-properties.md)  
  
## Category  
 General  
  
## Allowed Values  
  
|Edit box value|Description|  
|--------------------|-----------------|  
|Non-negative integer|Any value greater than one (1) will enable the corresponding element(s) in an instance message to occur up to that many times. To prohibit multiple occurrences, set the value of this property to one (1) or leave it blank. To prevent all occurrences, set the value of this property to zero (0).<br /><br /> The maximum value for Max Occurs is 4095. If you need a value greater than this, use "unbounded" as described below.|  
|"unbounded"<br /><br /> "*"|Use this value if you do not know how many loops you might have in an instance message and you do not want to lose any data. An asterisk (*) is a BizTalk Editor abbreviation for the literal string value "unbounded".|  
|No value|Use this property value to restore the behavior to the default value of one (1).|  
  
## Default Value  
 No value, indicating the default behavior associated with the value one (1).  
  
## XSD Persistence  
 As the value of the **maxOccurs** attribute of the element that corresponds to the selected node.  
  
> [!NOTE]
>  The literal string "unbounded", and not an asterisk (*), is persisted in the XSD.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a node of an appropriate type in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 When you set this property to any value other than **1**, BizTalk Mapper compiles the selected node as a looping record. If you configure this property with a value of **1**, BizTalk Mapper will not compile the selected node as a looping record.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)