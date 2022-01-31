---
description: "Learn more about: Advanced Functoids Reference"
title: Advanced Functoids Reference
TOCTitle: Advanced Functoids Reference
ms:assetid: 4b7a761f-510c-47ce-9506-4cb8e9ebba5c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560018(v=BTS.80)
ms:contentKeyID: 51527854
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Advanced Functoids Reference

Use **Advanced** functoids to create various types of data manipulation, such as implementing custom script, value mapping, and managing and extracting data from looping records.

For conceptual information about **Advanced** functoids, see [Advanced Functoids](/biztalk/core/advanced-functoids).

The following table shows the functoids in the **Advanced** category.

| Advanced functoid | Description |
|-------------------|-------------|
| :::image type="icon" source="images/Aa560747.313715e0-e73d-4806-941a-413d5ad1dee3(BTS.80).jpeg"::: [Assert](assert-functoid-reference.md) | Enables you to test your assumptions about conditions in a map. Assertions are tested in Development builds only. |
| :::image type="icon" source="images/Aa547061.0f578133-d730-4d60-bc4a-2832c31294b5(BTS.80).jpeg"::: [Index](index-functoid-reference.md) | Provides a way to extract a particular value from a sequence of repeating values by specifying the appropriate index. Indices can also have varying degrees of scope depending on hierarchy depth and levels indicated by the index.   |
| :::image type="icon" source="images/Aa560018.1c8ae190-aed0-49fc-b235-5c8b871b6b76(BTS.80).jpeg"::: [Iteration](iteration-functoid-reference.md) | For each repetition of a structure or value in an input instance message, outputs a monotonically increasing index. |
| :::image type="icon" source="images/Aa560018.1f70c94a-151c-4b07-9165-88873a0c33ff(BTS.80).jpeg"::: [Looping](looping-functoid-reference.md) | Used to explicitly indicate a looping relationship between a repeating structure in the source schema and a repeating structure in the destination schema. |
| :::image type="icon" source="images/Aa560018.8d9b71f3-8e19-4b2b-a393-3592b01e07f3(BTS.80).jpeg"::: [Mass Copy](mass-copy-functoid-reference.md) | Recursively copies all data in an input instance message, to arbitrary depth, that corresponds to a specified node in the source schema to the specified position in an output instance message. |
| :::image type="icon" source="images/Aa560952.061a0589-22a0-4f1b-8c75-4ba58bf042ac(BTS.80).jpeg"::: [Nil Value](nil-value-functoid-reference.md) | Sets the value of the destination node to **Nil**. |
| :::image type="icon" source="images/Aa577847.8a6ab6c8-4e8b-4a53-8d3c-98303756f851(BTS.80).jpeg"::: [Record Count](record-count-functoid-reference.md) | Outputs the number of times a specified repeating structure or value occurs in an input instance message. |
| :::image type="icon" source="images/Aa560018.bd458694-6168-4c8c-90d2-da4407485122(BTS.80).jpeg"::: [Scripting](scripting-functoid-reference.md) | Runs custom script to create content for an output instance message or input to another functoid. |
| :::image type="icon" source="images/Aa560018.4260373f-6d17-4b60-9fc5-661d0b829824(BTS.80).jpeg"::: [Table Extractor](table-extractor-functoid-reference.md) | Outputs the data associated with a specified column for each row of the table looping grid of a **Table Looping** functoid. |
| :::image type="icon" source="images/Aa559129.8f4b3620-4778-4d73-a60d-b11dea1766aa(BTS.80).jpeg"::: [Table Looping](table-looping-functoid-reference.md) | In conjunction with one or more **Table Extractor** functoids, creates a repeating structure in an output instance message by using constant values, values from an instance message, and values that are output from other functoids. |
| :::image type="icon" source="images/Aa560018.7853c31e-dc26-4ffa-9608-29352508e725(BTS.80).jpeg"::: [Value Mapping](value-mapping-functoid-reference.md) | Allows a Boolean value to control whether an entire structure or another single value in an input instance message gets copied to an output instance message. |
| :::image type="icon" source="images/Aa561516.0b7c29fa-4dbc-4497-9411-86c7d1b81387(BTS.80).jpeg"::: [Value Mapping (Flattening)](value-mapping-flattening-functoid-reference.md) | Allows a Boolean value to control whether an entire structure in an input instance message gets copied to an output instance message, flattening the input hierarchy in the process. |

## See Also

[Adding Advanced Functoids to a Map](/biztalk/core/adding-advanced-functoids-to-a-map)
