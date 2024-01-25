---
description: "Learn more about: Extended (BTS-XSD) Validation"
title: "Extended (BTS-XSD) Validation"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Extended (BTS-XSD) Validation
The EDI receive pipeline and EDI send pipeline perform extended validation only if the schema has been customized with elements whose data type is not an EDI data type. These added elements would not be validated by EDI validation, so will be covered by extended validation. Extended validation uses `System.Xml.XmlValidatingReader` and includes all checks that can be defined in a standard XSD.  
  
 You configure extended validation for all messages to or from a party. You do so by selecting the **Extended Validation** checkbox in the **Validation** page (under the **Transaction Set Settings** section for either X12 or EDIFACT), on the one-way agreement tab in the **Agreement Properties** dialog box. You can enable extension validation without enabling EDI validation, or vice versa.  
  
 Extended validation consists of the following checks:  
  
-   Data element requirement and allowed repetition  
  
-   Enumerations  
  
-   Data element length validation (min/max).  
  
> [!IMPORTANT]
>  Extended Validation for batched messages on the EDI send side is not supported.  
  
## See Also  
 [EDI Message Validation](../core/edi-message-validation.md)
