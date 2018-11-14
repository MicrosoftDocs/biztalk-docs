---
title: Get Common Value Functoid
TOCTitle: Get Common Value Functoid
ms:assetid: 14a33cfa-e27a-41f1-82d1-d074117d8990
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa558698(v=BTS.80)
ms:contentKeyID: 51526377
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Get Common Value Functoid

 

Use the **Get Common Value** functoid ( ![](images/Aa562112.e457cba1-6b35-4ef1-a872-19df042ea1cc(BTS.80).jpeg)) to retrieve a common value.

## Input

**Parameter 1:** A string of up to 50 characters that identifies the type of the object being referenced.

**Parameter 2:** A string of up to 50 characters that identifies the type of the application.

**Parameter 3:** A string of up to 50 characters that contains the application value.

## Output

**Output 1:** A string of up to 50 characters that contains the corresponding common value. If no such value is found, an empty string is returned.

## Remarks

If the object type (parameter 1) or the application type (parameter 2) is not valid, an exception is generated.

## See Also

[Database Functoids Reference](database-functoids-reference.md)  
[Database Functoids](https://msdn.microsoft.com/library/aa560892\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))  
[Format Message Functoid](format-message-functoid.md)  
[Get Application ID Functoid](get-application-id-functoid.md)  
[Get Application Value Functoid](get-application-value-functoid.md)  
[Get Common ID Functoid](get-common-id-functoid.md)  
[Set Common ID Functoid](set-common-id-functoid.md)

