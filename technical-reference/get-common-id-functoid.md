---
description: "Learn more about: Get Common ID Functoid"
title: Get Common ID Functoid
TOCTitle: Get Common ID Functoid
ms:assetid: d5d30c54-8b77-4623-8171-903b98edb9a1
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578629(v=BTS.80)
ms:contentKeyID: 51531530
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Get Common ID Functoid

 

Use the **Get Common ID** functoid ( ![Icon that shows the Get Common ID functoid.](images/Aa562112.26f78937-34c9-4149-9603-519109276d7c(BTS.80).jpeg)) to retrieve an identifier for a common object.

## Input

**Parameter 1:** A string of up to 50 characters that identifies the type of the object being referenced.

**Parameter 2:** A string of up to 50 characters that identifies the application instance.

**Parameter 3:** A string of up to 50 characters that identifies the application object.

## Output

**Output 1:** A string of up to 50 characters that identifies the corresponding common object. If no such object is found, an empty string is returned.

## Remarks

If the object type (parameter 1) or the application instance (parameter 2) is not valid, an exception is generated.

## See Also

[Database Functoids Reference](database-functoids-reference.md)  
[Database Functoids](https://msdn.microsoft.com/library/aa560892\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))  
[Format Message Functoid](format-message-functoid.md)  
[Get Application ID Functoid](get-application-id-functoid.md)  
[Get Application Value Functoid](get-application-value-functoid.md)  
[Get Common Value Functoid](get-common-value-functoid.md)  
[Set Common ID Functoid](set-common-id-functoid.md)

