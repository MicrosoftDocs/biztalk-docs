---
title: "Scripting Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Scripting functoids, about Scripting functoids"
  - "Scripting functoids, properties"
ms.assetid: d2bd405b-d432-492b-8557-de843c1c8f2f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Scripting Functoid Reference
Use the **Scripting** functoid ( ![](../core/media/advscript.gif "advscript")) to create content for an output instance message or input to another functoid.  
  
## Input  
 Depends on the design and implementation of the script. However, if your script will accept one or more arguments, make sure you choose the appropriate type and handle cases where the argument value may be null or the wrong type. For example, choose a string type if your functoid is expecting an integer and then convert the string into an integer after validation. This way, if the integer is missing, you can perform appropriate logic and avoid an exception.  
  
## Output  
 Depends entirely on the supplied script.  
  
## Remarks  
 Scripts associated with this functoid must meet one of the following criteria:  
  
-   Written in some form of .NET script (such as C# or Microsoft Visual Basic .NET), as XSLT, or as an XSLT call template.  
  
-   Resides in a separate assembly, in which case it must be strong-signed and registered in the global assembly cache.  
  
-   If a map uses Scripting functoid which has reference to an external assembly, then the test map works even without registering the assembly in GAC, provided the assembly is bin-placed in the same folder as the Mapper assembly.  
  
## See Also  
 [Advanced Functoids Reference](../core/advanced-functoids-reference.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Scripting Functoid](../core/scripting-functoid.md)   
 [How to Add Scripting Functoids to a Map](../core/how-to-add-scripting-functoids-to-a-map.md)