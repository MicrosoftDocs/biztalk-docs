---
description: "Learn more about: Set Common ID Functoid"
title: Set Common ID Functoid
TOCTitle: Set Common ID Functoid
ms:assetid: 180d7eda-421a-4ef4-9ed4-832fbc4643ea
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558788(v=BTS.80)
ms:contentKeyID: 51526459
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Set Common ID Functoid

 

Use the **Set Common ID** functoid ( ![Icon that represents the Set Common ID functoid.](images/Aa562112.6c2faac4-f20d-4d8c-8553-578c41c04eb9(BTS.80).jpeg)) to set and return an identifier for a common object.

## Input

**Parameter 1:** A string of up to 50 characters that identifies the type of the object being referenced.

**Parameter 2:** A string of up to 50 characters that identifies the application instance.

**Parameter 3:** A string of up to 50 characters that identifies the application object.

**Parameter 4:** An optional string of up to 50 characters that identifies the common object. An empty string for this parameter is treated the same as the parameter not being specified.

## Output

**Output 1:** A string of up to 50 characters that identifies the common object, and that is either the same identifier as the fourth parameter or, when the optional fourth parameter is not specified, an automatically generated string that identifies the common object.

## Remarks

If parameter 4, identifying the common object, is not specified, then a unique common identifier is generated and associated with the application identifier.

Only the first three parameters are required. If either of the first two parameters is not valid, an exception is generated.

An exception is also generated if either of the following conditions is encountered:

  - The indicated application object already has a common object associated with it.

  - The common object, as indicated by using the optional fourth parameter, is not found.

## See Also

[Database Functoids Reference](database-functoids-reference.md)  
[Database Functoids](https://msdn.microsoft.com/library/aa560892\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))  
[Format Message Functoid](format-message-functoid.md)  
[Get Application ID Functoid](get-application-id-functoid.md)  
[Get Application Value Functoid](get-application-value-functoid.md)  
[Get Common ID Functoid](get-common-id-functoid.md)  
[Get Common Value Functoid](get-common-value-functoid.md)

