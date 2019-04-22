---
title: Cumulative Minimum Functoid
TOCTitle: Cumulative Minimum Functoid
ms:assetid: 0dc39b45-0928-4fe9-a56f-f2d58665f81b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547362(v=BTS.80)
ms:contentKeyID: 51526215
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Cumulative Minimum Functoid

 

Use the **Cumulative Minimum** functoid ( ![](images/Aa561799.066f13a5-aa0c-4e9d-87ee-6667d9a3a39e(BTS.80).jpeg)) to determine the minimum value of a numeric value that recurs within corresponding instance messages.

## Input

**Parameter 1:** A link from a **Record**, **Field Element**, or **Field Attribute** node that contains a numeric value for which the minimum instance is sought.

**Parameter 2:** An optional numeric value that indicates the scope to which the accumulation should be performed. The default value is zero (0), indicating that the accumulation scope is the entire instance message.

## Output

**Output 1:** A numeric value that is the minimum value of the specified field or record values over the specified or default scope.

## Remarks

For more information about the scoping parameter, see [Cumulative Functoids Reference](cumulative-functoids-reference.md).

## See Also

[Cumulative Functoids Reference](cumulative-functoids-reference.md)  
[Cumulative Functoids](https://msdn.microsoft.com/library/aa561839\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

