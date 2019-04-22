---
title: Iteration Functoid Reference
TOCTitle: Iteration Functoid Reference
ms:assetid: 3ccd959f-93e9-46bc-93a3-af366d845db1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559704(v=BTS.80)
ms:contentKeyID: 51527498
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Iteration Functoid Reference

 

Use the **Iteration** functoid ( ![](images/Aa560018.1c8ae190-aed0-49fc-b235-5c8b871b6b76(BTS.80).jpeg)) to output the number of passes through a repeating structure in an input instance message as that structure is being processed.

## Input

**Parameter 1:** A link from a repeating structure in the source schema.

## Output

**Output 1:** A monotonically increasing number, starting at one (1), for each iteration through the specified repeating structure.

## Remarks

For example, if the **Iteration** functoid is connected to a **Record** node in the source schema and connected to a **Field Element** node named "book" in the destination schema, and in a particular instance message the corresponding input element occurs three times, the following output is produced:

```C#
<book>1</book>  
<book>2</book>  
<book>3</book>  
  
```

## See Also

[Advanced Functoids Reference](advanced-functoids-reference.md)  
[Advanced Functoids](https://msdn.microsoft.com/library/aa561121\(v=bts.80\))  
[Iteration Functoid](https://msdn.microsoft.com/library/aa559232\(v=bts.80\))  
[How to Add Iteration Functoids to a Map](https://msdn.microsoft.com/library/aa559120\(v=bts.80\))

