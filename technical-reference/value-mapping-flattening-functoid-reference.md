---
title: Value Mapping (Flattening) Functoid Reference
TOCTitle: Value Mapping (Flattening) Functoid Reference
ms:assetid: e03c96d0-9215-496b-ab53-a385f1cdcae0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561516(v=BTS.80)
ms:contentKeyID: 51532891
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Value Mapping (Flattening) Functoid Reference

 

Use the **Value Mapping (Flattening)** functoid ( ![](images/Aa561516.0b7c29fa-4dbc-4497-9411-86c7d1b81387(BTS.80).jpeg)) to allow a Boolean value to control whether another value gets mapped, flattening it in the process.

## Input

**Parameter 1:** Either of the strings "true" or "false", generally from the output of some other **Logical** functoid or from a variable Boolean field in the input instance message.

**Parameter 2:** A value that is output if parameter 1 is "true". This value can be from a link from a node in the source schema that represents simple content, the output from another functoid, or a constant input parameter.

## Output

**Output 1:** The value of the second parameter if the value of the first parameter is "true". If the value of the first parameter is not "true", the corresponding element or attribute in the output instance message is not created.

## Remarks

Determine whether to use the [Value Mapping](value-mapping-functoid-reference.md) functoid or the **Value Mapping (Flattening)** functoid based on the following characteristics of the relevant portions of the source and destination schemas:

  - **Value Mapping.** When both the source and the destination schemas define parallel repeating structures between which the relevant data is mapped.

  - **Value Mapping (Flattening).** When the source schema defines a repeating structure and the destination schema defines a flat structure, such that different instances of the repeating structure in the source schema are intended to be mapped into unique elements in the flat structure in the destination schema.


> [!NOTE]
> <P>The <STRONG>Looping</STRONG> and <STRONG>Value Mapping (Flattening)</STRONG> functoids should not be used together. If both are used together, it results in a compiled map that assumed there is no source looping dependency for the target nodes that are below the <STRONG>Looping</STRONG> functoid.</P>



## See Also

[Advanced Functoids Reference](advanced-functoids-reference.md)  
[Advanced Functoids](https://msdn.microsoft.com/library/aa561121\(v=bts.80\))  
[Value Mapping (Flattening) Functoid](https://msdn.microsoft.com/library/aa578572\(v=bts.80\))  
[Value Mapping Functoid](https://msdn.microsoft.com/library/aa559723\(v=bts.80\))  
[How to Add Value Mapping (Flattening) Functoids to a Map](https://msdn.microsoft.com/library/aa546740\(v=bts.80\))

