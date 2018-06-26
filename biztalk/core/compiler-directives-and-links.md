---
title: "Compiler Directives and Links | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "compilier directives"
  - "maps, compiling"
  - "BizTalk Mapper, compiler directives"
  - "links [maps], compiling"
ms.assetid: 1655e10c-af98-4100-849d-b8214f93cfe9
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Compiler Directives and Links
You can configure the following two compiler directives on a link-by-link basis:  
  
- What data from the input instance message is retrieved and copied as the relevant element or attribute value in the output instance message.  
  
  > [!NOTE]
  >  Data here includes the option to copy the name of the element or attribute itself, rather than any value associated with the element or attribute. Element and attribute names are not normally thought of as part of the data carried in an XML instance message.  
  
- How node-matching is performed between the source and destination schemas.  
  
  This section provides a detailed explanation of these options available for these directives.  
  
## In This Section  
  
-   [Data Transformation Configuration](../core/data-transformation-configuration.md)  
  
-   [Node-Hierarchy Level Matching](../core/node-hierarchy-level-matching.md)