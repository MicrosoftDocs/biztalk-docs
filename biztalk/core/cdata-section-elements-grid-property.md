---
title: "CDATA Section Elements (Grid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CDATA Section Elements property [grid pages]"
ms.assetid: fa4bf34f-8a0c-4569-a3d0-d632ff939a8c
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CDATA Section Elements (Grid Property)
Use the **CDATA Section Elements** property to specify a list of elements whose text node children should be output by using CDATA sections.  
  
## Category  
 Custom Header  
  
## Allowed Values  
 Any value that follows the **QName** (qualified name) naming convention. It can be a simple name or a name preceded by a namespace prefix and a colon.  
  
## Default Value  
 None.  
  
## Remarks  
 This property provides a value for the **cdata-section-elements** attribute of the XSL **output** element. For more information about this attribute, refer to the .NET Framework documentation.  
  
> [!NOTE]
>  You cannot undo or redo the **CDATA Section Elements**  property.  
  
 If you provide multiple values for this property, separate them with spaces.  
  
## See Also  
 [Grid Properties](../core/grid-properties.md)