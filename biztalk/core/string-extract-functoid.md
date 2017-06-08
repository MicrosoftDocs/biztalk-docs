---
title: "String Extract Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "String Extract functoids"
ms.assetid: ed1aa7b5-5261-4821-af9a-6f998d4360ee
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# String Extract Functoid
Use the **String Extract** functoid ( ![](../core/media/stringsubstrate.gif "stringsubstrate")) to extract a substring from the specified string.  
  
## Input  
 **Parameter 1:** The string from which to extract the substring.  
  
 **Parameter 2:** A numeric value that is the string position, starting at 1, of the first character of the substring to be extracted.  
  
 **Parameter 3:** A numeric value that is the string position, starting at 1, of the last character of the substring to be extracted.  
  
## Output  
 **Output 1:** A string that contains the requested substring, or an empty string if the requested substring cannot be extracted due to incorrect values for parameters 2 and/or 3. However, if parameter 3 exceeds the size of the string, a substring is still returned as though parameter 3 were set to the exactly the size of the string.  
  
## Remarks  
 String positions are counted starting from one (1).  
  
 You can use other string functoids, such as [Size](../core/size-functoid.md), to determine string characteristics, such as length, to avoid passing parameter values that are out-of-range.  
  
## See Also  
 [String Functoids Reference](../core/string-functoids-reference.md)   
 [String Functoids](../core/string-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)