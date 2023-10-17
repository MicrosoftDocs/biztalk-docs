---
description: "Learn more about: Agreement Properties Validation"
title: "Agreement Properties Validation"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Agreement Properties Validation
Agreement properties include checks for duplicate control numbers for interchanges, groups, or transaction sets. The EDI receive pipeline will perform these validations only if they are enabled in agreement properties. These validations include:  
  
-   Checking for a duplicate interchange control number (ISA13 in X12 or UNB5 in EDIFACT). You enter a time value (in days) to establish the valid time range for this check.  
  
-   Checking for a duplicate group control number in an interchange (GS6 in X12 or UNG5 in EDIFACT)  
  
-   Checking for a duplicate transaction set control number in a functional group (ST2 in X12 or UNH1 in EDIFACT)  
  
## See Also  
 [EDI Message Validation](../core/edi-message-validation.md)
