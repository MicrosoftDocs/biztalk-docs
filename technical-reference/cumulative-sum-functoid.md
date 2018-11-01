---
title: Cumulative Sum Functoid
TOCTitle: Cumulative Sum Functoid
ms:assetid: fd284a70-5f29-4631-974a-3f97a154f9b9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa562121(v=BTS.80)
ms:contentKeyID: 51533734
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Cumulative Sum Functoid

 

Use the **Cumulative Sum** functoid ( ![](images/Aa561799.a1343591-0bdc-48dd-929d-c9ddae9c5e86(BTS.80).jpeg)) to calculate the accumulated sum of a numeric value that recurs within corresponding instance messages.

## Input

**Parameter 1:** A link from a **Record**, **Field Element**, or **Field Attribute** node that contains a numeric value for which the accumulated sum is sought.

**Parameter 2:** An optional numeric value that indicates the scope to which the accumulation should be performed. The default value is zero (0), indicating that the accumulation scope is the entire instance message.

## Output

**Output 1:** A numeric value that is the accumulated sum of the specified field or record values over the specified or default scope.

## Remarks

For more information about the scoping parameter, see [Cumulative Functoids Reference](cumulative-functoids-reference.md).

## See Also

[Cumulative Functoids Reference](cumulative-functoids-reference.md)  
[Cumulative Functoids](https://msdn.microsoft.com/en-us/library/aa561839\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/en-us/library/aa560635\(v=bts.80\))

