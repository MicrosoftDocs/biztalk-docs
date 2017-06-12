---
title: "Default Child Order (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Default Child Order property [Flat File schemas]"
ms.assetid: 41c67f27-3511-4a63-ae68-7aa3589bea97
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Default Child Order (Node Property of Flat File Schemas)
Use the **Default Child Order** property to configure, for the entire schema, the default relationship between delimiters and the data they delimit.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Prefix**|Use this value when the delimiter appears before the data that it is delimiting.|  
|**Postfix**|Use this value when the delimiter appears after the data that it is delimiting.|  
|**Infix**|Use this value when the delimiter appears between different items of data, resulting in one less delimiter than when **Prefix** or **Postfix** is chosen.|  
|**Conditional Default**|Removes the corresponding annotation in the XSD representation of the schema, if any, resulting in the following default behavior for all **Record** nodes in the schema:<br /><br /> -   If a **Record** node has a tag identifier, then the child order will be prefix.<br />-   Otherwise, the child order will be infix.|  
  
## Default Value  
 **Conditional Default**  
  
## XSD Persistence  
 As the value of the **default_child_order** (="prefix", "postfix", or "infix") attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
 You can override the global setting established by this property by setting the [Child Order](../core/child-order-node-property-of-flat-file-schemas.md) property for individual **Record** nodes.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)   
 [Child Order (Node Property of Flat File Schemas)](../core/child-order-node-property-of-flat-file-schemas.md)