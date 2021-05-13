---
description: "Learn more about: Format Message Functoid"
title: Format Message Functoid
TOCTitle: Format Message Functoid
ms:assetid: 477cc8b5-fe76-4b82-baee-fbc5fda1f1d5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559909(v=BTS.80)
ms:contentKeyID: 51527768
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Format Message Functoid

 

Use the **Format Message** functoid ( ![Icon that represents the Format Message functoid.](images/Aa562112.70a6fb56-e342-4bd0-87ce-7cc77984928d(BTS.80).jpeg)) to return a formatted and localized string.

## Input

**Parameter 1:** A string that contains an identifier used to look up the message string. See remarks for additional information about the format of message strings, including replaceable arguments.

**Parameter 2:** A string that contains an identifier for the language of the message string;. for example, "en-us" for U.S. English.

**Parameter 3:** An optional string of up to 50 characters that identifies an application instance, and which is used with ID cross referencing for message string arguments. A null value can be used to indicate that no application instance is being supplied.

**Parameter 4:** An optional string of up to 50 characters that identifies an application type, and which is used with value cross referencing for message string arguments. A null value can be used to indicate that no application type is being supplied.

**Parameter 5:** If either parameter 3 or parameter 4 is provided, parameter 5 must be the corresponding lookup value. Otherwise, parameter 5 is an optional string that, if present, is substituted for the first replaceable argument in the message string.

**Parameter 6:** An optional string that, if present, is substituted for either the first or the second replaceable argument in the message string (depending on the values of parameters 3, 4, and 5).

**Parameters 7 – 13:** An optional string that, if present, is substituted for the next replaceable argument in the message string.

## Output

**Output 1:** A formatted string in the requested language with all of its replaceable arguments replaced with the provided substitution strings, including ID and value cross referencing where applicable.

## Remarks

Only the first two parameters are required. If either of the first two parameters is not valid, an exception is generated.

Message strings, as identified by the first parameter, are strings with replaceable arguments. The replaceable arguments within the string have the format "%n", where "n" is a monotonically increasing integer starting with one (1). For example, the following string has two replaceable arguments: "Operation %1 failed with code %2".

## See Also

[Database Functoids Reference](database-functoids-reference.md)  
[Database Functoids](https://msdn.microsoft.com/library/aa560892\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))  
[Get Application ID Functoid](get-application-id-functoid.md)  
[Get Application Value Functoid](get-application-value-functoid.md)  
[Get Common ID Functoid](get-common-id-functoid.md)  
[Get Common Value Functoid](get-common-value-functoid.md)  
[Set Common ID Functoid](set-common-id-functoid.md)

