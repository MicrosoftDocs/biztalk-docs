---
description: "Learn more about: Validation of Outgoing EDI Messages"
title: "Validation of Outgoing EDI Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 491303c0-b585-409e-a289-a2f6f9f82469
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Validation of Outgoing EDI Messages
When the EDI send pipeline processes a message to be sent, it performs a series of validations on the envelope and message data. Some of these processes are always performed; some are performed only if you enable them. These validations include the following:  
  
-   Schema validation of the transaction-set data elements against the message schema. This is always performed.  
  
-   Cross-field validation on transaction set data elements (X12-encoded messages only). This is performed if it is enabled in the message schema.  
  
-   EDI validation performed on transaction-set data elements. This is performed if enabled in agreement properties.  
  
-   Extended validation performed on transaction-set data elements. This is performed if enabled in agreement properties.  
  
-   Validation of the transaction sets within a single group based on the transaction set – group mapping, according to X12 standards. This is performed only when the **Inbound batch processing option** property is set to **Preserve Interchange - suspend Interchange on Error** or **Preserve Interchange - suspend Transaction Sets on Error**.  
  
## See Also  
 [EDI Structural Validation](../core/edi-structural-validation.md)   
 [Agreement Properties Validation](../core/agreement-properties-validation.md)   
 [EDI Type (Data Element) Validation](../core/edi-type-data-element-validation.md)   
 [Extended (BTS-XSD) Validation](../core/extended-bts-xsd-validation.md)   
 [Schema Validation](../core/schema-validation2.md)   
 [Cross Field-Segment Validation](../core/cross-field-segment-validation.md)
