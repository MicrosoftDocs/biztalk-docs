---
title: "Format Message Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Format Message functoids"
ms.assetid: 477cc8b5-fe76-4b82-baee-fbc5fda1f1d5
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Format Message Functoid
Use the **Format Message** functoid ( ![](../core/media/formatmessage.gif "formatmessage")) to return a formatted and localized string.  
  
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
 [Database Functoids Reference](../core/database-functoids-reference.md)   
 [Database Functoids](../core/database-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
 [Get Application ID Functoid](../core/get-application-id-functoid.md)   
 [Get Application Value Functoid](../core/get-application-value-functoid.md)   
 [Get Common ID Functoid](../core/get-common-id-functoid.md)   
 [Get Common Value Functoid](../core/get-common-value-functoid.md)   
 [Set Common ID Functoid](../core/set-common-id-functoid.md)