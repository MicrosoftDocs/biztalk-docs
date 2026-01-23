---
description: "Learn more about: Record Count Functoid Reference"
title: Record Count Functoid Reference
TOCTitle: Record Count Functoid Reference
ms:assetid: a380ed75-7726-4a74-9bc1-936369b1d886
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577847(v=BTS.80)
ms:contentKeyID: 51530228
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Record Count Functoid Reference

 

Use the **Record Count** functoid ( ![Icon that represents the Record Count functoid.](images/Aa577847.8a6ab6c8-4e8b-4a53-8d3c-98303756f851(BTS.80).jpeg)) to generate a count of the number of times a particular repeating structure occurs in an input instance message.

## Input

**Parameter 1:** A link from a node in the source schema. For this functoid to do something interesting, the structure in an input instance message that corresponds to this node must be repeating. Otherwise, the output is always one (1).

## Output

**Output 1:** A number that corresponds to the number of occurrences of the repeating structure in an input instance message that corresponds to the node specified by parameter 1.

## Remarks

You can also use the **Record Count** functoid to count repeating field elements. It is not restricted to records.

## See Also

[Advanced Functoids Reference](advanced-functoids-reference.md)  
[Advanced Functoids](https://msdn.microsoft.com/library/aa561121\(v=bts.80\))  
[Record Count Functoid](https://msdn.microsoft.com/library/aa561646\(v=bts.80\))  
[How to Add Record Count Functoids to a Map](https://msdn.microsoft.com/library/aa559757\(v=bts.80\))

