---
description: "Learn more about: Remove Application ID"
title: Remove Application ID
TOCTitle: Remove Application ID Functoid
ms:assetid: 4cdfef07-1b23-4844-ad86-28ddbf9bcf19
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560047(v=BTS.80)
ms:contentKeyID: 51527900
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Remove Application ID

 

Use the **Remove Application ID** functoid ( ![RemoveApplicationID functoid](images/Aa560047.12248c44-a162-48a7-b881-8876f21da260(BTS.80).jpeg "RemoveApplicationID functoid")) to remove an identifier for an application object.

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

