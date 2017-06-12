---
title: "Size Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Size functoids"
ms.assetid: eaf6f008-0025-4110-a391-fc3c92745129
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Size Functoid
Use the **Size** functoid ( ![](../core/media/stringsize.gif "stringsize")) to retrieve the length of the specified string.  
  
## Input  
 **Parameter 1:** A string for which the length is sought.  
  
## Output  
 **Output 1:** A numeric value that is the length of the string.  
  
## Remarks  
 The returned length represents the number of characters in the string, as returned by the **Length** method of the **String** class in the .NET framework. In some cases, for some East Asian languages, the number of glyphs you see on the screen for a particular string may not be equal to the length returned by this functoid for that same string.  
  
 The returned length includes pad characters.  
  
## See Also  
 [String Functoids Reference](../core/string-functoids-reference.md)   
 [String Functoids](../core/string-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)