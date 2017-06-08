---
title: "Envelope (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Envelope property [schemas]"
ms.assetid: b6333ccc-f8df-4078-90fe-c9b5be25f16c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Envelope (Node Property of All Schemas)
Use the **Envelope** property to configure whether the schema defines the structure of an envelope.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Yes**|Sets the **is_envelope** attribute to "yes", specifying that the selected schema represents an envelope.|  
|**No**|Sets the **is_envelope** attribute to "no", specifying that the selected schema does not represent an envelope.|  
|**(Default)**|Removes the **is_envelope** attribute, if present, specifying that the selected schema does not represent an envelope (same as **No**).|  
  
## Default Value  
 **(Default)**, resulting in no **is_envelope** attribute and specifying that the selected schema does not represent an envelope.  
  
## XSD Persistence  
 As the value of the **is_envelope** (= "yes" or "no") attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
 When you set this property to **Yes**, it means that the actual message content of the XML instance message (called the body of the message) is present somewhere inside the root **Record** node of this schema, as specified by the **Body XPath** property of that node. Therefore, you must also set additional properties based on a variety of conditions:  
  
-   Regardless of whether an envelope schema has a single root or multiple roots, setting the **Root Reference** property is not required.  
  
-   If an envelope schema has a single root, you must set the **Body XPath** property for that root.  
  
-   If an envelope schema has multiple roots and the **Root Reference** property is not set, you must set the **Body XPath** property for all roots.  
  
-   If an envelope schema has multiple roots and the **Root Reference** property is set, you must set the **Body XPath** property of the corresponding root **Record** node. You can optionally set the **Body XPath** property for the remaining roots.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)