---
title: "Receipt (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Receipt property [schemas]"
ms.assetid: 80f2054e-09a1-46b5-9695-b1fd6891c6e6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receipt (Node Property of All Schemas)
Use the **Receipt** property to configure whether the schema represents an inbound receipt message.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Yes**|Sets the **is_receipt** attribute to "yes", specifying that the selected schema represents an inbound receipt message. A correlator component is used to correlate an inbound receipt message with the outbound document for which it acknowledges receipt.|  
|**No**|Sets the **is_receipt** attribute to "no", specifying that the selected schema does not represent an inbound receipt message.|  
|**(Default)**|Removes the **is_receipt** attribute, if present, specifying that the selected schema does not represent an inbound receipt message (same as **No**).|  
  
## Default Value  
 **(Default)**, specifying that the selected schema does not represent an inbound receipt message.  
  
## XSD Persistence  
 As the value of the **is_receipt** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)