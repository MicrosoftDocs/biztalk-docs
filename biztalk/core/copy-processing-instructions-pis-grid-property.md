---
title: "Copy Processing Instructions (PIs) (Grid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Copy Processing Instructions (PIs) property [grid pages]"
  - "messages, processing"
ms.assetid: dadc1164-16c5-466c-9419-2395405d54aa
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Copy Processing Instructions (PIs) (Grid Property)
Use the **Copy Processing Instructions (PIs)** property to specify whether any processing instructions found in the input instance message should be copied to the output instance message during transformation.  
  
## Category  
 Custom Header  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**True**|Specifies that processing instructions should be copied from the input instance message to the output instance message.|  
|**False**|Specifies that processing instructions should not be copied from the input instance message to the output instance message.|  
  
## Default Value  
 **False**  
  
## Remarks  
 A processing instruction is an item in an XML file that is used to provide instructions to an application that processes the XML file. Within an XML file, processing instructions are delimited by "\<?" and "?>".  
  
> [!NOTE]
>  The Copy Processing Instructions property copies instructions only from one message to another, single message. Processing instructions cannot be copied from or to all of the parts in multi-part mappings (one-to-many or many-to-one).  
  
> [!NOTE]
>  You cannot undo or redo the **Copy Processing Instructions (PIs)** property.  
  
## See Also  
 [Grid Properties](../core/grid-properties.md)