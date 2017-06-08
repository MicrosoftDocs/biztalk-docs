---
title: "Child Order (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Child Order property [Flat File schemas]"
ms.assetid: 6de9f681-9087-48fa-985c-e18449da0820
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Child Order (Node Property of Flat File Schemas)
Use the **Child Order** property to configure the relationship between delimiters and the data they delimit.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Prefix**|Specifies that the delimiter appears before the data that it is delimiting.|  
|**Postfix**|Specifies that the delimiter appears after the data that it is delimiting.|  
|**Infix**|Specifies that the delimiter appears between different items of data, resulting in one less delimiter than when **Prefix** or **Postfix** is chosen.|  
|**Default Child Order**|Sets the **child_order** attribute to "default", specifying that the child order specified using the [Default Child Order](../core/default-child-order-node-property-of-flat-file-schemas.md) property should be used.|  
|**Conditional Default**|Removes the corresponding annotation in the XSD representation of the schema, if any, resulting in the following behavior:<br /><br /> -   If the **Record** node has a tag identifier, then the child order will be prefix.<br />-   Otherwise, the child order will be infix.|  
  
## Default Value  
 **Conditional Default**  
  
## XSD Persistence  
 As the value of the **child_order** (="prefix", "postfix", "infix", or "default") attribute of the **element/annotation/appinfo/recordInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you have:  
  
-   Selected a **Record** node (including a root **Record** node) in BizTalk Editor  
  
-   Set the **Structure** property of the selected **Record** node to **Delimited**  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)   
 [Default Child Order (Node Property of Flat File Schemas)](../core/default-child-order-node-property-of-flat-file-schemas.md)