---
title: "Preserve Delimiter For Empty Data (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Preserve Delimiter For Empty Data property [Flat File schemas]"
ms.assetid: 069d5a6d-1ff1-4028-889a-4e7dfc32425d
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Preserve Delimiter For Empty Data (Node Property of Flat File Schemas)
Use the **Preserve Delimiter For Empty Data** property to control whether empty records and/or fields within that record will still have delimiters present in instance messages.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Yes**|Specifies that both empty fields and empty records that are immediate children of the selected **Record** node should have their delimiters preserved.|  
|**No**|Specifies that neither empty fields nor empty records that are immediate children of the selected **Record** node should have their delimiters preserved.|  
  
## Default Value  
 **Yes**, specifying that both empty fields and empty records that are immediate children of the selected **Record** node should have their delimiters preserved.  
  
## XSD Persistence  
 As the value of the **preserve_delimiter_for_empty_data** (="true" for **Yes**, or "false" for **No**) attribute of the **element/annotation/appinfo/recordInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record** node (including a root **Record** node) in BizTalk Editor and you have:  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
-   Set the **Structure** property of the selected **Record** node to **Delimited**  
  
 When a field corresponding to a **Field Element** or **Field Attribute** node is entirely missing from an instance message, the corresponding delimiter will always be generated, regardless of the setting of this property, except when a Record follows a missing optional Field.  
  
> [!NOTE]
>  When a Record follows a missing optional Field, delimiters will not be preserved. For more information missing flat file delimiters, see [Delimiter Preservation and Suppression](../core/delimiter-preservation-and-suppression.md).  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)