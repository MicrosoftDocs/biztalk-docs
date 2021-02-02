---
description: "Learn more about: Cumulative Average Functoid"
title: Cumulative Average Functoid
TOCTitle: Cumulative Average Functoid
ms:assetid: b8ed38e8-6674-40c1-af26-26ab79bc3a81
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578299(v=BTS.80)
ms:contentKeyID: 51530778
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Cumulative Average Functoid

 

Use the **Cumulative Average** functoid ( ![](images/Aa578299.ab36f1e7-3341-464c-a171-f93bce223bbe(BTS.80).jpeg)) to calculate the accumulated average of a numeric value that recurs within corresponding instance messages.

## Input

**Parameter 1:** A link from a **Record**, **Field Element**, or **Field Attribute** node that contains a numeric value for which the accumulated average is sought.

**Parameter 2:** An optional numeric value that indicates the scope to which the accumulation should be performed. The default value is zero (0), indicating that the accumulation scope is the entire input instance message.

## Output

**Output 1:** A numeric value that is the accumulated average value of the specified field or record values over the specified or default scope.

## Remarks

For more information about the scoping parameter, see [Cumulative Functoids Reference](cumulative-functoids-reference.md).

## See Also

[Cumulative Functoids Reference](cumulative-functoids-reference.md)  
[Cumulative Functoids](https://msdn.microsoft.com/library/aa561839\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

