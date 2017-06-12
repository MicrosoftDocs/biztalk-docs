---
title: "Schema Type (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schema Type property [schemas]"
ms.assetid: b56b7f04-2e28-40c0-8f47-60902b3a9173
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Type (Node Property of All Schemas)
Use the **Schema Type** property to specify the type of the schema being edited as either a document schema or a property schema.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Document**|Sets the **schema_type** attribute of the **schemaInfo** annotation to "document", specifying that the selected schema represents an instance message.|  
|**Property**|Sets the **schema_type** attribute of the **schemaInfo** annotation to "property", specifying that the selected schema represents one or more properties that you intend to promote. You cannot set the **Schema Type** property to **Property** unless the schema conforms to the requirements of property schemas.|  
|**(Default)**|Removes the **schema_type** attribute, if present, which is equivalent to specifying that the selected schema represents a message (same as **Document**).|  
  
## Default Value  
 **(Default)**, which is the same as specifying the value **Document**.  
  
## XSD Persistence  
 As the value of the **schema_type** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
 For detailed instructions about how to create a property schema, see [How to Create Property Schemas](../core/how-to-create-property-schemas.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)