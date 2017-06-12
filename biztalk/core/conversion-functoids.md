---
title: "Conversion Functoids | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Conversion functoids, about Conversion functoids"
  - "Hexadecimal functoids"
  - "functoid types, Hexadecimal"
  - "Hexadecimal functoids, about Hexadecimal functoids"
  - "Conversion functoids"
  - "functoid types, Conversion"
ms.assetid: 0cd7abcf-f524-4e85-b8d5-d6123767490f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Conversion Functoids
**Conversion** functoids are used to convert between numbers and their ASCII equivalents, and to convert base 10 numbers to their base 8 and base 16 equivalents.  
  
 All of the conversion functoids take a single input parameter.  
  
> [!NOTE]
>  Due to changes in the underlying type system, the **Conversion** functoids in this version of BizTalk Mapper produce slightly different results than those produced in previous versions. For example, in previous versions of BizTalk Mapper an input value of -20 to the **Hexadecimal** functoid resulted in an output of 0xFFEC. In this version, the same input value of -20 will result in an output of 0xFFFFFFEC.  
  
 The **Conversion** functoids are: [ASCII to Character](../core/ascii-to-character-functoid.md), [Character to ASCII](../core/character-to-ascii-functoid.md), [Hexadecimal](../core/hexadecimal-functoid.md), and [Octal](../core/octal-functoid.md).  
  
## See Also  
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
 [Conversion Functoids Reference](../core/conversion-functoids-reference.md)