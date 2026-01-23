---
description: "Learn more about: Size Functoid"
title: Size Functoid
TOCTitle: Size Functoid
ms:assetid: eaf6f008-0025-4110-a391-fc3c92745129
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561736(v=BTS.80)
ms:contentKeyID: 51533187
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
---

# Size Functoid

 

Use the **Size** functoid ( ![Icon that represents the Size functoid.](images/Aa561736.a3a598ef-7c99-4233-bb27-837654716336(BTS.80).jpeg)) to retrieve the length of the specified string.

## Input

**Parameter 1:** A string for which the length is sought.

## Output

**Output 1:** A numeric value that is the length of the string.

## Remarks

The returned length represents the number of characters in the string, as returned by the **Length** method of the **String** class in the .NET framework. In some cases, for some East Asian languages, the number of glyphs you see on the screen for a particular string may not be equal to the length returned by this functoid for that same string.

The returned length includes pad characters.

## See Also

[String Functoids Reference](string-functoids-reference.md)  
[String Functoids](https://msdn.microsoft.com/library/aa559399\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

