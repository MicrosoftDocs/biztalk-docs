---
title: "Body XPath (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Body XPath property [schemas]"
ms.assetid: 69ea9e35-fa36-4bbf-bc74-74d7938edd22
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Body XPath (Node Property of All Schemas)
Use the **Body XPath** property to identify the portion of the schema that defines the body of the message associated with the selected root **Record** node in an envelope schema.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Parse  
  
## Allowed Values  
 XPath values are specified using the schema subtree displayed within the **Body XPath** dialog box, which can be opened using the ellipsis (**...**) button located to the right of the **Body XPath** property value field.  
  
> [!NOTE]
>  Only canonical XPath values are supported by the BizTalk Server engine. They must be constructed using the default schema format (for example: `/*[local-name()="..." and namespace-uri()="..."]`). Also note that `position()="..."` specifiers cannot be used in the XPath.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of the **body_xpath** attribute of the **schema/annotation/appinfo/recordInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a root **Record** node in an envelope schema in BizTalk Editor (envelope schemas are those schemas for which you have set the [Envelope](../core/envelope-node-property-of-all-schemas.md) property of the **Schema** node to **Yes**).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)