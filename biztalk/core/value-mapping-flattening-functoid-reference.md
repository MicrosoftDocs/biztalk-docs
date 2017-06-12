---
title: "Value Mapping (Flattening) Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Value Mapping (Flattening) functoids"
ms.assetid: e03c96d0-9215-496b-ab53-a385f1cdcae0
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Value Mapping (Flattening) Functoid Reference
Use the **Value Mapping (Flattening)** functoid ( ![](../core/media/advvaluemapflattening.gif "advvaluemapflattening")) to allow a Boolean value to control whether another value gets mapped, flattening it in the process.  
  
## Input  
 **Parameter 1:** Either of the strings "true" or "false", generally from the output of some other **Logical** functoid or from a variable Boolean field in the input instance message.  
  
 **Parameter 2:** A value that is output if parameter 1 is "true". This value can be from a link from a node in the source schema that represents simple content, the output from another functoid, or a constant input parameter.  
  
## Output  
 **Output 1:** The value of the second parameter if the value of the first parameter is "true". If the value of the first parameter is not "true", the corresponding element or attribute in the output instance message is not created.  
  
## Remarks  
 Determine whether to use the [Value Mapping](../core/value-mapping-functoid-reference.md) functoid or the **Value Mapping (Flattening)** functoid based on the following characteristics of the relevant portions of the source and destination schemas:  
  
-   **Value Mapping.** When both the source and the destination schemas define parallel repeating structures between which the relevant data is mapped.  
  
-   **Value Mapping (Flattening).** When the source schema defines a repeating structure and the destination schema defines a flat structure, such that different instances of the repeating structure in the source schema are intended to be mapped into unique elements in the flat structure in the destination schema.  
  
> [!NOTE]
>  The **Looping** and **Value Mapping (Flattening)** functoids should not be used together. If both are used together, it results in a compiled map that assumed there is no source looping dependency for the target nodes that are below the **Looping** functoid.  
  
## See Also  
 [Advanced Functoids Reference](../core/advanced-functoids-reference.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md)   
 [Value Mapping Functoid](../core/value-mapping-functoid.md)   
 [How to Add Value Mapping (Flattening) Functoids to a Map](../core/how-to-add-value-mapping-flattening-functoids-to-a-map.md)