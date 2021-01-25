---
description: "Learn more about: Scripting Functoid Reference"
title: Scripting Functoid Reference
TOCTitle: Scripting Functoid Reference
ms:assetid: d2bd405b-d432-492b-8557-de843c1c8f2f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578566(v=BTS.80)
ms:contentKeyID: 51531562
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Scripting Functoid Reference

 

Use the **Scripting** functoid ( ![](images/Aa560018.bd458694-6168-4c8c-90d2-da4407485122(BTS.80).jpeg)) to create content for an output instance message or input to another functoid.

## Input

Depends on the design and implementation of the script. However, if your script will accept one or more arguments, make sure you choose the appropriate type and handle cases where the argument value may be null or the wrong type. For example, choose a string type if your functoid is expecting an integer and then convert the string into an integer after validation. This way, if the integer is missing, you can perform appropriate logic and avoid an exception.

## Output

Depends entirely on the supplied script.

## Remarks

Scripts associated with this functoid must meet one of the following criteria:

  - Written in some form of .NET script (such as C\# or Microsoft Visual Basic .NET), as XSLT, or as an XSLT call template.

  - Resides in a separate assembly, in which case it must be strong-signed and registered in the global assembly cache.

  - If a map uses Scripting functoid which has reference to an external assembly, then the test map works even without registering the assembly in GAC, provided the assembly is bin-placed in the same folder as the Mapper assembly.

## See Also

[Advanced Functoids Reference](advanced-functoids-reference.md)  
[Advanced Functoids](https://msdn.microsoft.com/library/aa561121\(v=bts.80\))  
[Scripting Functoid](https://msdn.microsoft.com/library/aa561729\(v=bts.80\))  
[How to Add Scripting Functoids to a Map](https://msdn.microsoft.com/library/aa561749\(v=bts.80\))

