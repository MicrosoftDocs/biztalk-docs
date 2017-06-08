---
title: "EDI Structural Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87086614-5616-441d-915c-2979c63c6e2f
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Structural Validation
EDI specifications for both X12 and EDIFACT encoding define specific rules and conventions for the structure of EDI interchanges. The EDI Disassembler in the EDIReceivePipeline verifies that the envelope of each received message complies with these structural rules. The EDISendPipeline builds each message to be sent in accordance with these rules and validates the envelope before sending.  
  
 The structural validation ensures that the required headers and trailers are present. The structural integrity checks include segment and loop ordering and count checks. These checks are always performed to ensure that the document will parse or serialize correctly. This validation is performed even if the **EDI Type Validation** and/or **Extended Validation** options are disabled. An interchange that fails the basic structural validations will be suspended, even if the **EDI Type Validation** and/or **Extended Validation** options are disabled.  
  
 The values of the data elements within the headers and trailers, and how the headers/trailers and data elements are separated, are determined by the agreement. These are validated through schema validation.  
  
 For more information about the envelope and the contents within each set of headers and trailers, see [EDI Message Structure](../core/edi-message-structure.md).  
  
## See Also  
 [EDI Message Validation](../core/edi-message-validation.md)