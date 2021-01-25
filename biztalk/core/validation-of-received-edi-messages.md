---
description: "Learn more about: Validation of Received EDI Messages"
title: "Validation of Received EDI Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c56a3c0-042e-4611-8131-d51098064f0f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Validation of Received EDI Messages
When the EDI receive pipeline processes an incoming message, it performs a series of validations on the envelope and message data. Some of these processes are always performed; some are performed only if you enable them. These validations include the following:  
  
-   **The validations that are always performed are**:  
  
    -   Validation of the structure of the interchange envelope.  
  
    -   Validation of the envelope against trading partner agreement (or fallback agreement if no agreement is defined).  
  
    -   Schema validation of the envelope against the control schema.  
  
    -   Schema validation of the transaction-set data elements against the message schema.  
  
    -   Validation of the types of transaction sets within a single group based on the transaction set -group mapping provided by X12 standards.  
  
-   **The validations that are performed only if enabled are**:  
  
    -   EDI validation performed on transaction-set data elements. This is performed if enabled in the agreement properties.  
  
    -   Extended validation performed on transaction-set data elements. This is performed if enabled in the agreement properties.  
  
    -   Cross-field validation on transaction set data elements (X12-encoded messages only). This is performed if enabled in the message schema.  
  
## See Also  
 [EDI Structural Validation](../core/edi-structural-validation.md)   
 [Agreement Properties Validation](../core/agreement-properties-validation.md)   
 [EDI Type (Data Element) Validation](../core/edi-type-data-element-validation.md)   
 [Extended (BTS-XSD) Validation](../core/extended-bts-xsd-validation.md)   
 [Schema Validation](../core/schema-validation2.md)   
 [Cross Field-Segment Validation](../core/cross-field-segment-validation.md)
