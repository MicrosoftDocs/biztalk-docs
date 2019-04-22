---
title: Subtraction Functoid
TOCTitle: Subtraction Functoid
ms:assetid: 188efc20-0c07-4d32-86af-ec0854d641a5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa558800(v=BTS.80)
ms:contentKeyID: 51526503
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Subtraction Functoid

 

Use the **Subtraction** functoid ( ![](images/Aa558800.3ff3db5e-b89d-46fa-aadb-3966ac9eea56(BTS.80).jpeg)) to calculate the result of subtracting up to 99 numeric values from another numeric value.

## Input

**Parameter 1:** A numeric value from which is to be subtracted the combined values of all of the other specified numeric values.

**Parameters 2 – 100:** Additional numeric values, the combined value of which is to be subtracted from the value specified by parameter 1.

## Output

**Output 1:** A numeric value that is the result of subtracting all subsequent specified numeric values from the numeric value specified by parameter 1.

## Remarks

Consider the following example of a result produced by this functoid:

  - Parameter 1, P1, is 20.

  - Parameter 2, P2, is 3.

  - Parameter 3, P3, is 2.

  - Parameter 4, P4, is 4.

  - Parameter 5, P5, is 6.

P1 – (P2 + P3 + P4 + P5) = Output or 20 – (3 + 2 + 4 + 6) = 5

## See Also

[Mathematical Functoids Reference](mathematical-functoids-reference.md)  
[Mathematical Functoids](https://msdn.microsoft.com/library/aa559213\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

