---
title: "SWIFT Error Codes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "errors, error codes"
  - "error codes"
  - "technical reference, error codes"
ms.assetid: 03699986-965b-4a28-ab2e-09f110fb4db6
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Error Codes
SWIFT defines many network-imposed validations against the set of financial (FIN) messages. Each validation relates to a type of check against the contents of the message, and is associated with a three-character error code. The first character of the error code implies the class of the problem detected, and is a letter. The remaining two characters denote the detail of the error (when combined with the class) and always appear as a two-digit code.  
  
 The following table lists the letter designations, validation type, rule change associated with each class of error, and whether or not the class of error is supported.  
  
|Class|Validation type and rule change|Supported?|  
|-----------|-------------------------------------|----------------|  
|**C, D, E**|Semantic validation rules 0-299|Supported|  
|**Knn**|Invalid code word in field *nn*|Supported|  
|**M50**|Message length exceeded|Unsupported|  
|**M60**|Non-SWIFT character encountered|Supported|  
|**T**|Text validation error codes|Supported|  
|**G**|Specific error codes for message user group (MUG) Textval rules|Unsupported|  
|**B**|Special error codes for value-added services|Unsupported|  
  
 All SWIFT errors should be referenced in the *SWIFT User Handbook*. For more information and for a complete list of SWIFT error codes, refer to the *Message Format Validation Rules* volume of the *SWIFT User Handbook*. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] implements the rules in the September 2003 edition of this publication. You can access the SWIFT Web site at [http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885).  
  
 There are some codes which are defined by A4SWIFT. These error codes are used in the validation/network rules created and implemented by A4SWIFT, so there is no corresponding error code defined by SWIFT for such rules. Below table shows the error code and corresponding case in which the error is thrown. is the particular field which throws the error.  
  
|Error Code|Description|  
|----------------|-----------------|  
|A4SWIFT001|The first character of multiline field cannot be ':' or '-' character for second and  subsequent lines.|  
|A4SWIFT002|Field contains invalid value.|  
  
> [!NOTE]
>  [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes support for some legacy messages, because internal applications might use these messages. Therefore, A4SWIFT maintains the associated SWIFT rules and error codes.