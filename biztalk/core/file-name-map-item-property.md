---
title: "File Name (Map Item Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "File Name property [maps]"
ms.assetid: 4dc855d5-c1ca-4ccd-a505-21eeca211c85
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Name (Map Item Property)
Use the **File Name** property to change the name of the map file, which is also the name of the map itself.  
  
## Category  
 Miscellaneous  
  
## Allowed Values  
 Valid file names can be entered as for the value of this property.  
  
## Default Value  
 The name of the map when it was created. By default, map names have the form "Map*N*.btm", where "*N*" is a monotonically increasing number starting with one (1).  
  
## Remarks  
 The value of the [Type Name](../core/type-name-map-item-property.md) property does not change automatically when you change the value of the **File Name** property. If you want to keep them the same, you must change the **Type Name** property manually.