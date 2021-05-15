---
description: "Learn more about: Looping Functoid Reference"
title: Looping Functoid Reference
TOCTitle: Looping Functoid Reference
ms:assetid: 776041c2-1f1d-415d-ac86-89d40dedc103
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560883(v=BTS.80)
ms:contentKeyID: 51529035
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Looping Functoid Reference

 

Use the **Looping** functoid ( ![Icon that represents the Looping functoid.](images/Aa560018.1f70c94a-151c-4b07-9165-88873a0c33ff(BTS.80).jpeg)) to combine multiple repeating structures in an input instance message into a single repeating structure in the output instance message.

## Input

**Parameters 1 – 100:** A link from at least one repeating node in the source schema, and optionally, links from other repeating nodes in the source schema.

## Output

**Output 1:** A link to a single repeating node in the destination schema.

## Remarks

The input and output links for the **Looping** functoid define the repeating structures in an input instance message that are combined into a single repeating structure in an output instance message. However, additional links are required from nodes within the repeating nodes in the source schema to the appropriate nodes within the repeating node in the destination schema. Without these additional links, the repeating structures are combined, but without any of the data that they contain.

For example, if there are two input links and their corresponding structures repeat 5 and 10 times, respectively, in a particular input instance message, the corresponding structure in the output instance message repeats 15 times.

The **Looping** functoid can be useful in a number of ways, but it is somewhat more complicated to set up correctly than many other functoids.For more information about the **Looping** functoid, see the [Looping Functoid](https://msdn.microsoft.com/library/aa559012\(v=bts.80\)).

Under certain conditions, some functoids might not behave as expected when they are used in a map with a **Looping** functoid. If a functoid meets the following conditions, it does not produce the expected results when used with the **Looping** functoid:

  - The functoid has more than one input link.

  - Two or more of the functoid input links are linked to child fields of the input records to the **Looping** functoid, where the child fields are not siblings.

  - The functoid has an output link that is linked to a child field of the output record of the **Looping** functoid.

  - There is a logical filter in effect that makes the loop occur only when the logical condition evaluates to **True**.


> [!NOTE]
> <P>The Looping functoid should not be used with the Value Mapping (Flattening) functoid. If both are used together, it results in a compiled map that assumed there is no source looping dependency for the target nodes that are below the <STRONG>Looping</STRONG> functoid.</P>



## See Also

[Advanced Functoids Reference](advanced-functoids-reference.md)  
[Advanced Functoids](https://msdn.microsoft.com/library/aa561121\(v=bts.80\))  
[Looping Functoid](https://msdn.microsoft.com/library/aa559012\(v=bts.80\))  
[How to Add Looping Functoids to a Map](https://msdn.microsoft.com/library/aa578162\(v=bts.80\))

