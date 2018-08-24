---
title: Logical OR Functoid
TOCTitle: Logical OR Functoid
ms:assetid: 58398fbf-0445-4b49-826c-0339dde69c50
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560272(v=BTS.80)
ms:contentKeyID: 51528200
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Logical OR Functoid

 

Use the **Logical OR** functoid ( ![](images/Aa560272.82f62b4d-fa44-4ce1-98cb-75030ae40a59(BTS.80).jpeg)) to determine whether any of the specified input parameters evaluate to **True**.

## Input

**Parameter 1:** A value that can be evaluated as either **True** or **False**.

**Parameters 2 – 100:** Values that can be evaluated as either **True** or **False**.

## Output

**Output 1:** The Boolean value **True** if any of the specified input parameters evaluate to **True**; the Boolean value **False** otherwise.

## Remarks

Input parameter values can be in a variety of data types (string, numeric, or logical), although passing strings to this functoid does not yield a meaningful result. For more information about how the **Logical** functoids handle input parameters of different types, see [Logical Functoids Reference](logical-functoids-reference.md).

## See Also

[Logical Functoids Reference](logical-functoids-reference.md)  
[Logical Functoids](https://msdn.microsoft.com/en-us/library/aa561580\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/en-us/library/aa560635\(v=bts.80\))

