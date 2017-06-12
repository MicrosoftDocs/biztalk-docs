---
title: "Link Source (Link Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Link Source property [schema links]"
ms.assetid: 0b1a4d5e-d19c-4ef6-8250-07ed2638fa57
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Link Source (Link Property)
Use the **Link Source** property to view the XPath of the node in the source schema, or the type of the functoid, that is the source of the selected link.  
  
## Category  
 General  
  
## Allowed Values  
  
|Value|Description|  
|-----------|-----------------|  
|XPath of a node in the destination schema|When the left end of the selected link is attached to a node in the source schema, this property shows the XPath to that node.|  
|Name of a functoid|When the left end of the selected link is attached to a functoid in a grid page, this property shows the type of that functoid, such as **Logical OR** or **Addition**.|  
  
## Remarks  
 This property is read-only.  
  
## See Also  
 [Link Properties](../core/link-properties.md)