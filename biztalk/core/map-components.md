---
title: "Map Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "file types, maps"
  - "BizTalk Mapper, output"
  - "maps, file type"
  - "maps, file contents"
  - "BizTalk Mapper, file type"
  - "maps, components"
ms.assetid: be438d21-80a8-49d8-bd08-d85618ab23de
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Map Components
Map files (having a .btm extension) store most of the components of a map. Items stored in the file include:  
  
- References to source and destination schemas  
  
- Links, including the link properties  
  
- Functoids with their properties such as input parameters  
  
- Other miscellaneous properties such as those associated with the grid and the map itself.  
  
  Although BizTalk Mapper compiles the map in the .btm file into an Extensible Stylesheet Transformations (XSLT) file, the XSLT is not part of the file. BizTalk Mapper produces the XSLT for the map only when you compile the project or when you validate the map. BizTalk Mapper packages the XSLT as part of the project assembly.  
  
## See Also  
 [Maps](../core/maps.md)   
 [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md)