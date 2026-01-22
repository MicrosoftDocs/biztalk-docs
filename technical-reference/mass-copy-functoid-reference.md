---
description: "Learn more about: Mass Copy Functoid Reference"
title: Mass Copy Functoid Reference
TOCTitle: Mass Copy Functoid Reference
ms:assetid: 7172d6d3-41d5-425b-9c80-19b064a4dca2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560775(v=BTS.80)
ms:contentKeyID: 51528879
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
---

# Mass Copy Functoid Reference

 

Use the **Mass Copy** functoid ( ![Icon that represents the Mass Copy functoid.](images/Aa560018.8d9b71f3-8e19-4b2b-a393-3592b01e07f3(BTS.80).jpeg)) to recursively copy all data in an input instance message, to arbitrary depth, that corresponds to a specified node in the source schema to the position in an output instance message that is specified by the output link.

## Input

**Parameter 1:** A link from a **Record** or **Field Element** node in the source schema, which has an arbitrarily complex child node structure within it.

## Output

**Output 1:** A link to a node in the destination schema, indicating the position within an output instance message into which to copy the element structure from the input instance message.

## Remarks

One way to understand the **Mass Copy** functoid is to consider that you can completely map input instance messages to output instance messages, where both types of messages are described by identical schemas, by linking the root node of the source schema to the root node of the destination schema.

This functoid is useful for mapping an **Any Element** or **Any Attribute** node from the source schema to the destination schema. For example, if you have a **Record** node named **Src** in the source schema and a **Record** node named **Dst** in the destination schema, and both of them have an **Any Element** or **Any Attribute** child node, then you can use the **Mass Copy** functoid to recursively copy the entire structure in an input instance message that corresponds to **Src** to the location in the output instance message that corresponds to **Dst**. To accomplish this, drag a **Mass Copy** functoid onto a grid page, connect the **Record** node named **Src** to the **Mass Copy** functoid to serve as its input parameter, and connect the **Mass Copy** functoid to the **Record** node named **Dst** to serve as the output of the functoid.

In general, you can use the **Mass Copy** functoid in this same way if the **Record** nodes **Src** and **Dst**, from the example above, have exactly the same structure in the source and destination schemas, respectively, regardless of whether the **Any Element** or **Any Attribute** nodes are present in those structures.

## See Also

[Advanced Functoids Reference](advanced-functoids-reference.md)  
[Advanced Functoids](https://msdn.microsoft.com/library/aa561121\(v=bts.80\))  
[Mass Copy Functoid](https://msdn.microsoft.com/library/aa559187\(v=bts.80\))  
[How to Add Mass Copy Functoids to a Map](https://msdn.microsoft.com/library/aa559086\(v=bts.80\))

