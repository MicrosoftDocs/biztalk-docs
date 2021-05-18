---
description: "Learn more about: Logical Existence Functoid"
title: Logical Existence Functoid
TOCTitle: Logical Existence Functoid
ms:assetid: 2ce33c5d-8384-4b82-b929-add0e5519c53
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559386(v=BTS.80)
ms:contentKeyID: 51527072
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Logical Existence Functoid

 

Use the **Logical Existence** functoid ( ![Icon that represents the Logical Existence functoid.](images/Aa559386.484702af-934c-4017-9b5a-c2d9fc94be51(BTS.80).jpeg)) to determine whether the **Record**, **Field Element**, or **Field Attribute** node that is linked to it exists in a particular input instance message.

## Input

**Parameter 1:** A link from a **Record**, **Field Element**, or **Field Attribute** node in the source schema that may or may not exist in a particular input instance message.

## Output

**Output 1:** The Boolean value **True** if the element or attribute that corresponds to the **Record**, **Field Element**, or **Field Attribute** node that is linked to this functoid exists in a particular input instance message; the Boolean value **False** otherwise.

## Remarks

The node in the source schema to which this functoid is linked must be a node that corresponds to an actual element or attribute in an instance message.

## See Also

[Logical Functoids Reference](logical-functoids-reference.md)  
[Logical Functoids](https://msdn.microsoft.com/library/aa561580\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

