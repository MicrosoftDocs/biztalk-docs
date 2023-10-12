---
title: "SWIFT error codes in BizTalk Server"
description: View the class and validation types for the SWIFT Accelerator in BizTalk Server
ms.custom: ""
ms.date: "08/16/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SWIFT Error Codes
SWIFT defines many network-imposed validations against the set of financial (FIN) messages. Each validation relates to a type of check against the contents of the message, and is associated with a three-character error code. The first character of the error code implies the class of the problem detected, and is a letter. The remaining two characters denote the detail of the error (when combined with the class) and always appear as a two-digit code.

## Class of errors
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

 All SWIFT errors should be referenced in the *SWIFT User Handbook*. For more information and for a complete list of SWIFT error codes, refer to the *Message Format Validation Rules* volume of the *SWIFT User Handbook*. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] implements the rules in the September 2003 edition of this publication. You can access the SWIFT Web site at [https://go.microsoft.com/fwlink/?LinkId=27885](https://go.microsoft.com/fwlink/?LinkId=27885).

## Validation errors
 There are some codes which are defined by A4SWIFT. These error codes are used in the validation/network rules created and implemented by A4SWIFT, so there is no corresponding error code defined by SWIFT for such rules. Below table shows the error code and corresponding case in which the error is thrown. is the particular field which throws the error.

|Error Code|Description|
|----------------|-----------------|
|A4SWIFT001|The first character of multiline field cannot be ':' or '-' character for second and  subsequent lines.|
|A4SWIFT002|Field contains invalid value.|

> [!NOTE]
>  [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes support for some legacy messages, because internal applications might use these messages. Therefore, A4SWIFT maintains the associated SWIFT rules and error codes.

## More good info
[Troubleshooting: Issues and Resolutions](troubleshooting-issues-and-resolutions1.md)
[Known Issues](known-issues5.md)
[Common terms and definitions](glossary6.md)