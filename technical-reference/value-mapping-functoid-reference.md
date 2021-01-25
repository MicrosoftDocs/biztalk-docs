---
description: "Learn more about: Value Mapping Functoid Reference"
title: Value Mapping Functoid Reference
TOCTitle: Value Mapping Functoid Reference
ms:assetid: e9c6e5ca-cedf-4e43-bbcc-fb8c2d880525
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561705(v=BTS.80)
ms:contentKeyID: 51533146
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Value Mapping Functoid Reference

 

Use the **Value Mapping** functoid ( ![](images/Aa560018.7853c31e-dc26-4ffa-9608-29352508e725(BTS.80).jpeg)) to allow a Boolean value to control whether another value gets mapped.

## Input

**Parameter 1:** Either of the strings "true" or "false", generally from the output of some other **Logical** functoid or from a variable Boolean field in the input instance message.

**Parameter 2:** A value that is output if parameter 1 is "true". This value can be from a link from a node in the source schema that represents simple content, the output from another functoid, or a constant input parameter.

## Output

**Output 1:** The value of the second parameter if the value of the first parameter is "true". If the value of the first parameter is not "true", the corresponding element or attribute in the output instance message is not created.

## Remarks

Determine whether to use the **Value Mapping** functoid or the [Value Mapping (Flattening)](value-mapping-flattening-functoid-reference.md) functoid based on the following characteristics of the relevant portions of the source and destination schemas:

  - **Value Mapping.** When both the source and the destination schemas define parallel repeating structures between which the relevant data is mapped.

  - **Value Mapping (Flattening).** When the source schema defines a repeating structure and the destination schema defines a flat structure, such that different instances of the repeating structure in the source schema are intended to be mapped into unique elements in the flat structure in the destination schema.

## See Also

[Advanced Functoids Reference](advanced-functoids-reference.md)  
[Advanced Functoids](https://msdn.microsoft.com/library/aa561121\(v=bts.80\))  
[Value Mapping Functoid](https://msdn.microsoft.com/library/aa559723\(v=bts.80\))  
[Value Mapping (Flattening) Functoid](https://msdn.microsoft.com/library/aa578572\(v=bts.80\))  
[How to Add Value Mapping Functoids to a Map](https://msdn.microsoft.com/library/aa548039\(v=bts.80\))  
[How to Add Value Mapping (Flattening) Functoids to a Map](https://msdn.microsoft.com/library/aa546740\(v=bts.80\))

