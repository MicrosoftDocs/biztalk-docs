---
title: "Value Mapping Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Value Mapping functoids"
ms.assetid: e9c6e5ca-cedf-4e43-bbcc-fb8c2d880525
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Value Mapping Functoid Reference
Use the **Value Mapping** functoid ( ![](../core/media/advvaluemap.gif "advvaluemap")) to allow a Boolean value to control whether another value gets mapped.  
  
## Input  
 **Parameter 1:** Either of the strings "true" or "false", generally from the output of some other **Logical** functoid or from a variable Boolean field in the input instance message.  
  
 **Parameter 2:** A value that is output if parameter 1 is "true". This value can be from a link from a node in the source schema that represents simple content, the output from another functoid, or a constant input parameter.  
  
## Output  
 **Output 1:** The value of the second parameter if the value of the first parameter is "true". If the value of the first parameter is not "true", the corresponding element or attribute in the output instance message is not created.  
  
## Remarks  
 Determine whether to use the **Value Mapping** functoid or the [Value Mapping (Flattening)](../core/value-mapping-flattening-functoid-reference.md) functoid based on the following characteristics of the relevant portions of the source and destination schemas:  
  
-   **Value Mapping.** When both the source and the destination schemas define parallel repeating structures between which the relevant data is mapped.  
  
-   **Value Mapping (Flattening).** When the source schema defines a repeating structure and the destination schema defines a flat structure, such that different instances of the repeating structure in the source schema are intended to be mapped into unique elements in the flat structure in the destination schema.  
  
## See Also  
 [Advanced Functoids Reference](../core/advanced-functoids-reference.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Value Mapping Functoid](../core/value-mapping-functoid.md)   
 [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md)   
 [How to Add Value Mapping Functoids to a Map](../core/how-to-add-value-mapping-functoids-to-a-map.md)   
 [How to Add Value Mapping (Flattening) Functoids to a Map](../core/how-to-add-value-mapping-flattening-functoids-to-a-map.md)