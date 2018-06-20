---
title: "XSD Element Groups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XSLT, XSLT variations"
  - "BizTalk Mapper, XSLT variations"
  - "maps, groups"
  - "Choice Group node"
  - "XSD element groups"
  - "XSLT, warnings"
ms.assetid: a6ea22cb-6066-480e-8a2a-75fade3e5970
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XSD Element Groups
The use of certain structures in a schema may create variations in the Extensible Stylesheet Language Transformations (XSLT) that BizTalk Mapper generates.  
  
 This can occur when you include a schema in your map that defines sequence, choice, or all element groups. For example, if you use a schema that includes a **Choice Group** node, it is possible for you to create a map that requires two or more of the children of the **Choice Group** node to appear in an output instance message. In this case, BizTalk Mapper displays a warning when you compile the map. The warning tells you that only one of the required fields you have mapped may be populated in the same iteration of the parent loop at run time. BizTalk Mapper does not give you an error message stating that your mapping logic is incorrect.  
  
 Another situation in which you might generate variations in the XSLT is when the following conditions are met:  
  
- **Record A** has a child **Field Element B**.  
  
- **Record A** and child **Field Element B** occur once.  
  
- **Record A** is part of a **Choice Group** that repeats.  
  
  In this situation, BizTalk Mapper generates XSLT that contains iteration logic to handle the possibility of the many variations of the source records.  
  
> [!NOTE]
>  You must be explicit with respect to mappings involving groups. For example, if a destination schema contains a **Choice Group** node with child nodes A and B, it is not valid to have A and B simultaneously on the same iteration of their parent group. BizTalk Mapper does not prevent you from creating mappings that are not valid. Therefore, you must use logical functoids to set up mappings in which A and B can never occur at the same time.  
  
## See Also  
 [Maps](../core/maps.md)   
 [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md)