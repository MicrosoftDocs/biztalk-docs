---
title: "Indent (Grid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Indent property [grid pages]"
  - "Indent property [grid pages], about Indent property"
ms.assetid: acc8c9a7-64af-42bf-873e-a05169c7ca5e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Indent (Grid Property)
Use the **Indent** property to specify whether the XML in destination instance messages produced by using this map will be indented for improved readability.  
  
## Category  
 Custom Header  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Yes**|Specifies that any destination instance messages produced by using this map will be indented for improved readability.|  
|**No**|Specifies that any destination instance messages produced by using this map will not be indented for improved readability.|  
  
## Default Value  
 Blank, indicating the same behavior as the **No** setting: Indentation will not be performed.  
  
## Remarks  
 This property provides a value for the **indent** attribute of the XSL **output** element. For more information about this attribute, refer to the .NET Framework documentation.  
  
> [!NOTE]
>  You cannot undo or redo the **Indent** property.  
  
## See Also  
 [Grid Properties](../core/grid-properties.md)