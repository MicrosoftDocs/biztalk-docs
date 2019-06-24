---
title: Cumulative Maximum Functoid
TOCTitle: Cumulative Maximum Functoid
ms:assetid: f24cf94a-10dd-4f8f-bcf7-d2b43f49a697
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561894(v=BTS.80)
ms:contentKeyID: 51533388
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Cumulative Maximum Functoid

 

Use the **Cumulative Maximum** functoid ( ![](images/Aa561894.eafb0c35-4d1c-4454-a475-0a605a839e2f(BTS.80).jpeg)) to determine the maximum value of a numeric value that recurs within corresponding instance messages.

## Input

**Parameter 1:** A link from a **Record**, **Field Element**, or **Field Attribute** node that contains a numeric value for which the maximum instance is sought.

**Parameter 2:** An optional numeric value that indicates the scope to which the accumulation should be performed. The default value is zero (0), indicating that the accumulation scope is the entire input instance message.

## Output

**Output 1:** A numeric value that is the maximum value of the specified field or record values over the specified or default scope.

## Remarks

For more information about the scoping parameter, see [Cumulative Functoids Reference](cumulative-functoids-reference.md).

## See Also

[Cumulative Functoids Reference](cumulative-functoids-reference.md)  
[Cumulative Functoids](https://msdn.microsoft.com/library/aa561839\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

