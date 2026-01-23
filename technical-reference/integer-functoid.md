---
description: "Learn more about: Integer Functoid"
title: Integer Functoid
TOCTitle: Integer Functoid
ms:assetid: 5ae6d0b3-3cf1-4089-909a-f675281dfeae
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560329(v=BTS.80)
ms:contentKeyID: 51528265
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Integer Functoid


Use the **Integer** functoid ( ![Icon that represents the Integer functoid.](images/Aa560329.93d37f07-a527-4d12-8872-d7856e652c34(BTS.80).jpeg)) to return the integer portion of a numeric input parameter.

## Input

**Parameter 1:** A numeric value for which the integer portion is sought.

## Output

**Output 1:** An integer value that is the integer portion of the specified real number.

## Remarks

This functoid removes the decimal point of a number and any digits to the right of the decimal point. Therefore, it is pointless to call this functoid if you know that the input value can never contain a decimal point.

## See Also

[Mathematical Functoids Reference](mathematical-functoids-reference.md)  
[Mathematical Functoids](https://msdn.microsoft.com/library/aa559213\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))  
[Round Functoid](round-functoid.md)


