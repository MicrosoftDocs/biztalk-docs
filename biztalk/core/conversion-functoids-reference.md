---
title: "Conversion Functoids Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Conversion functoids"
  - "functoid types, Conversion"
ms.assetid: b77f6dd9-9a0e-460c-8b17-a1d3bec7212d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Conversion Functoids Reference
Use **Conversion** functoids to perform a variety of standard character and numeric base conversion calculations.  
  
> [!IMPORTANT]
>  Because Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] uses the underlying functionality of the .NET Framework, the results produced by some of the **Conversion** functoids vary from the equivalent functoids in earlier versions of BizTalk Server. For example, in earlier versions of BizTalk Mapper an input value of -20 to the **Hexadecimal** functoid resulted in an output of FFEC. In this version, the same input value of -20 results in an output of FFFFFFEC. You should test your maps thoroughly to ensure that you are getting the results you expect.  
  
 For conceptual information about **Conversion** functoids, see [Conversion Functoids](../core/conversion-functoids.md).  
  
 The following table shows the functoids in the **Conversion** category.  
  
|Conversion functoid|Description|  
|-------------------------|-----------------|  
|![](../core/media/conversionchr.gif "conversionchr") [ASCII to Character](../core/ascii-to-character-functoid.md)|Determines the character equivalent of a value interpreted as ASCII.|  
|![](../core/media/conversionascii.gif "conversionascii") [Character to ASCII](../core/character-to-ascii-functoid.md)|Determines the ASCII equivalent of the specified character.|  
|![](../core/media/conversionhex.gif "conversionhex") [Hexadecimal](../core/hexadecimal-functoid.md)|Converts a decimal number to its hexadecimal equivalent.|  
|![](../core/media/conversionoct.gif "conversionoct") [Octal](../core/octal-functoid.md)|Converts a decimal number to its octal equivalent.|  
  
## See Also  
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)