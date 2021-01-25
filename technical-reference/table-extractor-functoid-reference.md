---
description: "Learn more about: Table Extractor Functoid Reference"
title: Table Extractor Functoid Reference
TOCTitle: Table Extractor Functoid Reference
ms:assetid: edb1c912-bdaf-4989-b61f-7bd8806f9566
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561789(v=BTS.80)
ms:contentKeyID: 51533233
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Table Extractor Functoid Reference

 

Use the **Table Extractor** functoid ( ![](images/Aa560018.4260373f-6d17-4b60-9fc5-661d0b829824(BTS.80).jpeg)) to output the data associated with a specified column for each row of the table looping grid of the specified **Table Looping** functoid.

## Input

**Parameter 1:** An output link from a **Table Looping** functoid.

**Parameter 2:** The column number of the table looping grid from which this functoid is meant to retrieve data.

## Output

**Output 1:** A set of values retrieved through the specified column of the table looping grid associated with the specified **Table Looping** functoid, where the number of values in the set is the number of rows in the table looping grid.

## Remarks

You must use this functoid in conjunction with the **Table Looping** functoid.

This functoid may output multiple values, one per row in the table looping grid associated with the **Table Looping** functoid specified by the first input parameter.

## See Also

[Advanced Functoids Reference](advanced-functoids-reference.md)  
[Advanced Functoids](https://msdn.microsoft.com/library/aa561121\(v=bts.80\))  
[Table Looping and Table Extractor Functoids](https://msdn.microsoft.com/library/aa559310\(v=bts.80\))  
[How to Add Table Looping and Table Extractor Functoids to a Map](https://msdn.microsoft.com/library/aa559694\(v=bts.80\))

