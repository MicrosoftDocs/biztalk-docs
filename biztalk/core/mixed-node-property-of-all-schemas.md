---
title: "Mixed (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Mixed property [schemas]"
  - "Mixed property [schemas], about Mixed property"
ms.assetid: a7823467-992e-40cf-9f82-2fba22a157c9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Mixed (Node Property of All Schemas)
Use the **Mixed** property to specify that character data or text might appear mixed with subelements within the element corresponding to the selected **Record** node in instance messages.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Advanced  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**True**|Sets the **mixed** attribute of the **complexType** element to "true", specifying that the corresponding content in an instance message will be mixed; that is substructure and content can both occur.|  
|**False**|Removes the **mixed** attribute of the **complexType** element, specifying that the instance messages corresponding to the selected **Record** node will have either substructure or content, but not both.|  
  
## Default Value  
 **False**, specifying that the instance messages corresponding to the selected **Record** node will have either substructure or content, but not both.  
  
## XSD Persistence  
 As the value of the **mixed** attribute of the **complexType** element that is a child of the element that corresponds to the selected **Record** node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node, including root **Record** nodes, in BizTalk Editor.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 HTML provides a very common example of mixed substructure and content. The paragraph tags in the following HTML example contain mixed content:  
  
 \<P>The full moon \<EM>always\</EM> rises at sunset, more or less.\</P>  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)