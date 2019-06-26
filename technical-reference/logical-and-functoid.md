---
title: Logical AND Functoid
TOCTitle: Logical AND Functoid
ms:assetid: 5fef25b1-8f1f-4056-80d0-02438362da1d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560432(v=BTS.80)
ms:contentKeyID: 51528416
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Logical AND Functoid

 

Use the **Logical AND** functoid ( ![](images/Aa560432.41ec41a2-63f0-407e-b3ee-9fa613cfd516(BTS.80).jpeg)) to determine whether all of the specified input parameters evaluate to **True**.

## Input

**Parameter 1:** A value that can be evaluated as either **True** or **False**.

**Parameters 2 – 100:** Values that can be evaluated as either **True** or **False**.

## Output

**Output 1:** The Boolean value **True** if all of the specified input parameters evaluate to **True**; the Boolean value **False** otherwise.

## Remarks

Input parameter values can be in a variety of data types (string, numeric, or logical), although passing strings to this functoid does not yield a meaningful result. For more information about how the **Logical** functoids handle input parameters of different types, see [Logical Functoids Reference](logical-functoids-reference.md).

## See Also

[Logical Functoids Reference](logical-functoids-reference.md)  
[Logical Functoids](https://msdn.microsoft.com/library/aa561580\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

