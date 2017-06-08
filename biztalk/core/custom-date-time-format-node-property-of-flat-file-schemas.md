---
title: "Custom Date-Time Format (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Custom Date/Time Format property [schemas]"
ms.assetid: 83d3e688-40bc-4547-9ef1-c0f0554201df
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Custom Date-Time Format (Node Property of Flat File Schemas)
Use the **Custom Date/Time Format** property to configure the date/time format found in the flat files for which this schema defines the structure.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 You can configure this property with almost any time and date format, except for Julian dates. The drop-down list provides various choices, but you can also type a different format of your choosing.  
  
 Allowable separators include dash (-), slash (/), and period (.).  
  
## Default Value  
 No value, resulting in no annotation being added to the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **datetime_format** attribute of the **fieldInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you have:  
  
-   Selected a **Field Element** or **Field Attribute** node in BizTalk Editor  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
-   Set the data type of the selected **Field Element** or **Field Attribute** node to a date, time, or date/time type  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)