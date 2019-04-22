---
title: Logical Date Functoid
TOCTitle: Logical Date Functoid
ms:assetid: 9cff7543-f240-4ff4-aba1-64f963b4eb42
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577573(v=BTS.80)
ms:contentKeyID: 51530011
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Logical Date Functoid

 

Use the **Logical Date** functoid ( ![](images/Aa577573.d77fb1a1-4472-4830-8e02-43cf3b396d9e(BTS.80).jpeg)) to determine whether the input parameter is a date.

## Input

**Parameter 1:** A string that may or may not be interpretable as an ISO-8601 formatted date.

## Output

**Output 1:** The Boolean value **True** if the input parameter is determined to be a date; the Boolean value **False** otherwise.

## Remarks

BizTalk Mapper, and XML in general, require date and time values to be specified in ISO-8601 format. However, this functoid will return the Boolean value **True** for any date format that is acceptable to the .NET **Convert.ToDateTime** method using invariant culture.

## See Also

[Logical Functoids Reference](logical-functoids-reference.md)  
[Logical Functoids](https://msdn.microsoft.com/library/aa561580\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

