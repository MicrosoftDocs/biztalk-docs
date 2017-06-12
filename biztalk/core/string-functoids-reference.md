---
title: "String Functoids Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "functoid types, String"
  - "String functoids"
ms.assetid: dfaf1813-21bf-4000-9010-845788c9cb45
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# String Functoids Reference
Use **String** functoids to manipulate strings in standard ways.  
  
> [!IMPORTANT]
>  Because Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the underlying functionality of the .NET Framework, the results produced by some of the **String** functoids may vary from the equivalent functoids in earlier versions of BizTalk Server. For example, string lengths are counted in characters rather than in bytes, which can differ for character encodings that use more than one byte per character. In such cases, the calculated length of the string may differ from the apparent length of a displayed string. You should test your maps thoroughly to ensure that you are getting the results you expect.  
  
 For conceptual information about **String** functoids, see [String Functoids](../core/string-functoids.md).  
  
 The following table shows the functoids in the **String** category.  
  
|String functoid|Description|  
|---------------------|-----------------|  
|![](../core/media/stringlowercase.gif "stringlowercase") [Lowercase](../core/lowercase-functoid.md)|Converts any uppercase characters in a string to lowercase.|  
|![](../core/media/stringsize.gif "stringsize") [Size](../core/size-functoid.md)|Retrieves the length of the specified string.|  
|![](../core/media/stringconcatenate.gif "stringconcatenate") [String Concatenate](../core/string-concatenate-functoid.md)|Concatenates the specified strings, in the order given.|  
|![](../core/media/stringsubstrate.gif "stringsubstrate") [String Extract](../core/string-extract-functoid.md)|Extracts a substring from the specified string.|  
|![](../core/media/stringfind.gif "stringfind") [String Find](../core/string-find-functoid.md)|Retrieves the starting position of a specified substring within a specified string.|  
|![](../core/media/stringleft.gif "stringleft") [String Left](../core/string-left-functoid.md)|Retrieves a specified number of characters from the start of a string.|  
|![](../core/media/stringlefttrim.gif "stringlefttrim") [String Left Trim](../core/string-left-trim-functoid.md)|Removes leading white space characters from a specified string.|  
|![](../core/media/stringright.gif "stringright") [String Right](../core/string-right-functoid.md)|Retrieves a specified number of characters from the end of a string.|  
|![](../core/media/stringrighttrim.gif "stringrighttrim") [String Right Trim](../core/string-right-trim-functoid.md)|Removes trailing white space characters from a specified string.|  
|![](../core/media/stringuppercase.gif "stringuppercase") [Uppercase](../core/uppercase-functoid.md)|Converts any lowercase characters in a string to uppercase.|  
  
## See Also  
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)