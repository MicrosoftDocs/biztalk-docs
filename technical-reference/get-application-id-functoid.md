---
description: "Learn more about: Get Application ID Functoid"
title: Get Application ID Functoid
TOCTitle: Get Application ID Functoid
ms:assetid: 5cf8cb55-6d17-4e5a-b654-9bee51e0cd89
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560375(v=BTS.80)
ms:contentKeyID: 51528320
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Get Application ID Functoid

 

Use the **Get Application ID** functoid ( ![Icon that represents the Get Application ID functoid.](images/Aa562112.96ae57bf-a9fd-4756-b802-0ccc2fbedfc3(BTS.80).jpeg)) to retrieve an identifier for an application object.

## Input

**Parameter 1:** A string of up to 50 characters that identifies the type of the object being referenced.

**Parameter 2:** A string of up to 50 characters that identifies the application instance.

**Parameter 3:** A string of up to 50 characters that identifies the common object.

## Output

**Output 1:** A string of up to 50 characters that identifies the corresponding application object. If no such object is found, an empty string is returned.

## Remarks

If the object type (parameter 1) or the application instance (parameter 2) is not valid, an exception is generated.

## See Also

[Database Functoids Reference](database-functoids-reference.md)  
[Database Functoids](https://msdn.microsoft.com/library/aa560892\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))  
[Format Message Functoid](format-message-functoid.md)  
[Get Application Value Functoid](get-application-value-functoid.md)  
[Get Common ID Functoid](get-common-id-functoid.md)  
[Get Common Value Functoid](get-common-value-functoid.md)  
[Set Common ID Functoid](set-common-id-functoid.md)

