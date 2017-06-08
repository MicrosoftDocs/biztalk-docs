---
title: "Source Links (Link Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Links property [schema links]"
ms.assetid: 9dc062d9-5de5-4e8f-a493-98ff4976c6b9
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Source Links (Link Property)
Use the **Source Links** property to specify the source of the data that will be copied to the destination of the link.  
  
## Category  
 Compiler  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Copy Name**|Specifies that the name of the node that is the source of the link is to be copied to the destination of the link.|  
|**Copy Text Value**|Specifies that the value of the node that is the source of the link is to be copied to the destination of the link.|  
|**Copy Text and Subcontent Value**|The value corresponding to the record node, and the value of all its child nodes, and their child nodes, in the source schema (element data and attribute values) are combined as the value of the linked node in the destination schema. For example, \<Node>Hello\<Name>John\</Name>Smith\</Node> would result in "Hello John Smith".|  
  
## Default Value  
 **Copy Text Value**  
  
## See Also  
 [Link Properties](../core/link-properties.md)