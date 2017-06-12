---
title: "Link Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "link properties [BizTalk Mapper]"
  - "grid properties [BizTalk Mapper], links"
  - "schemas, links"
  - "grid pages, BizTalk Mapper"
ms.assetid: a3a16232-507c-4536-9584-de483a9bf220
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Link Properties
The grid pages of BizTalk Mapper graphically depict the structure of the data transformation defined by the map. A link appears as a single line that makes one of the following connections:  
  
-   A node in the source schema to a node in the destination schema  
  
-   A node in the source schema to a functoid  
  
-   A functoid to a node in the destination schema  
  
-   One functoid to another functoid, which is known as cascading functoids  
  
 Links depict a transformation, or a step in the transformation, of data from a source instance message into a destination instance message. The left end of the link depicts the source of the transformation (step) and the right end of the link depicts the destination, or target, of the transformation (step).  
  
> [!NOTE]
>  When working with links and link properties, the words "destination" and "target" are used interchangeably.  
  
 The following table describes the properties of links.  
  
|Property name|Category|Description|  
|-------------------|--------------|-----------------|  
|[Label](../core/label-link-property.md)|General|Provides a descriptive name for the link that is useful for input links to the **Table Looping** functoid.|  
|[Link Source](../core/link-source-link-property.md)|General|Allows the source (left end) of the link to be examined in a non-graphical manner.|  
|[Link Target](../core/link-target-link-property.md)|General|Allows the destination (right end) of the link to be examined in a non-graphical manner.|  
|[Source Links](../core/source-links-link-property.md)|Compiler|Specifies the source of the data that will be copied to the destination of the link.|  
|[Target Links](../core/target-links-link-property.md)|Compiler|Specifies the type of node hierarchy matching associated with the link and controls how auto-linking is performed.|