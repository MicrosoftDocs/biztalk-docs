---
title: Cumulative Concatenate Functoid
TOCTitle: Cumulative Concatenate Functoid
ms:assetid: f04c493c-d150-4f80-aca9-9b77889b6b3f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561837(v=BTS.80)
ms:contentKeyID: 51533294
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Cumulative Concatenate Functoid

 

Use the **Cumulative Concatenate** functoid ( ![](images/Aa561799.96cb173a-f7b9-4042-a525-1e1f7475d54e(BTS.80).jpeg)) to concatenate multiple instances of a string value that recurs within corresponding instance messages.

## Input

**Parameter 1:** A link from a **Record**, **Field Element**, or **Field Attribute** node that contains a string value for which the accumulated concatenation is sought.

**Parameter 2:** An optional numeric value that indicates the scope to which the accumulation should be performed. The default value is zero (0), indicating that the accumulation scope is the entire input instance message.

## Output

**Output 1:** A string value that is the accumulated concatenation of the specified field or record values over the specified or default scope.

## Remarks

For more information about the scoping parameter, see [Cumulative Functoids Reference](cumulative-functoids-reference.md).

## See Also

[Cumulative Functoids Reference](cumulative-functoids-reference.md)  
[Cumulative Functoids](https://msdn.microsoft.com/library/aa561839\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

