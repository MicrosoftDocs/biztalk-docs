---
title: Round Functoid
TOCTitle: Round Functoid
ms:assetid: a0993b70-e388-470f-bbe7-b40f61595486
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577673(v=BTS.80)
ms:contentKeyID: 51530128
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Round Functoid

 

Use the **Round** functoid ( ![](images/Aa577673.ff25c636-ba90-404f-a911-eee519eade0c(BTS.80).jpeg)) to round the specified numeric input parameter to the nearest specified number of decimal places.

## Input

**Parameter 1:** A numeric value to be rounded to the nearest number of decimal places, as specified by parameter 2.

**Parameter 2:** A numeric value that is a (presumably small) whole number representing the number of decimal places to which the number specified by parameter 1 will be rounded.

## Output

**Output 1:** A numeric value that is the result of rounding the number specified by parameter 1 to the number of decimal places specified by parameter 2.

## Remarks

If parameter 2 is zero (0) or not provided, the result is a whole number.

This functoid uses banker or even rounding. For example, if the second parameter is 0 for whole number rounding, then 1.5 rounds to 2, while 4.5 rounds to 4.

## See Also

[Mathematical Functoids Reference](mathematical-functoids-reference.md)  
[Mathematical Functoids](https://msdn.microsoft.com/en-us/library/aa559213\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/en-us/library/aa560635\(v=bts.80\))  
[Integer Functoid](integer-functoid.md)

