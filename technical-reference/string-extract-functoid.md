---
description: "Learn more about: String Extract Functoid"
title: String Extract Functoid
TOCTitle: String Extract Functoid
ms:assetid: ed1aa7b5-5261-4821-af9a-6f998d4360ee
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561774(v=BTS.80)
ms:contentKeyID: 51533241
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# String Extract Functoid

 

Use the **String Extract** functoid ( ![](images/Aa561774.05f857b9-4210-44aa-844b-e08b5aeef95b(BTS.80).jpeg)) to extract a substring from the specified string.

## Input

**Parameter 1:** The string from which to extract the substring.

**Parameter 2:** A numeric value that is the string position, starting at 1, of the first character of the substring to be extracted.

**Parameter 3:** A numeric value that is the string position, starting at 1, of the last character of the substring to be extracted.

## Output

**Output 1:** A string that contains the requested substring, or an empty string if the requested substring cannot be extracted due to incorrect values for parameters 2 and/or 3. However, if parameter 3 exceeds the size of the string, a substring is still returned as though parameter 3 were set to the exactly the size of the string.

## Remarks

String positions are counted starting from one (1).

You can use other string functoids, such as [Size](size-functoid.md), to determine string characteristics, such as length, to avoid passing parameter values that are out-of-range.

## See Also

[String Functoids Reference](string-functoids-reference.md)  
[String Functoids](https://msdn.microsoft.com/library/aa559399\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

