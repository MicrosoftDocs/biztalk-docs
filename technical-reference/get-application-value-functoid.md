---
description: "Learn more about: Get Application Value Functoid"
title: Get Application Value Functoid
TOCTitle: Get Application Value Functoid
ms:assetid: af38c0b4-113e-49ee-9795-bf3f18a8aa96
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578092(v=BTS.80)
ms:contentKeyID: 51530549
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Get Application Value Functoid

 

Use the **Get Application Value** functoid ( ![Icon that represents the Get Application functoid.](images/Aa562112.90056a7f-8635-49bd-bb2c-c0646a9aff1f(BTS.80).jpeg)) to retrieve an application value.

## Input

**Parameter 1:** A string of up to 50 characters that identifies the type of the object being referenced.

**Parameter 2:** A string of up to 50 characters that identifies the type of the application.

**Parameter 3:** A string of up to 50 characters that contains the common value.

## Output

**Output 1:** A string of up to 50 characters that contains the corresponding application value. If no such value is found, an empty string is returned.

## Remarks

If the object type (parameter 1) or the application type (parameter 2) is not valid, an exception is generated.

## See Also

[Database Functoids Reference](database-functoids-reference.md)  
[Database Functoids](https://msdn.microsoft.com/library/aa560892\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))  
[Format Message Functoid](format-message-functoid.md)  
[Get Application ID Functoid](get-application-id-functoid.md)  
[Get Common ID Functoid](get-common-id-functoid.md)  
[Get Common Value Functoid](get-common-value-functoid.md)  
[Set Common ID Functoid](set-common-id-functoid.md)

