---
title: "Data Type ID in HL7 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data types, data type ID"
  - "data types, messages"
  - "messages, data types"
ms.assetid: d1412886-ff0b-4333-b01e-1c3ae45240e2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Type ID in HL7
In the case of HL7 V2.1, the data type ID is a placeholder for undefined data types. The following are examples of its usage:  
  
- The data type in the form of an ST field is SI (Sequence ID).  
  
- The data type in the form of an NM field is composite fields.  
  
  The following are examples of specifically defined composite data types:  
  
- CK: Composite ID with check digit. For example:  
  
  ```  
  |128952^6^M11|  
  ```  
  
- CN: Composite ID number and name. For example:  
  
  ```  
  |12372^RIGGINS^JOHN^""^MD|  
  |12372|  
  |^RIGGINS^JOHN^""^MD|  
  ```  
  
- CQ: Composite quantity with units. For example:  
  
  ```  
  |123.7^ML|  
  ```  
  
- CE: Coded element. For example:  
  
  ```  
  |54.21^Laparoscopy^I9C^42112^^AS4|  
  ```  
  
  This data type is localized and site-defined. Additionally, HL7 V2.1 does not provide the coverage for this data type in the HL7 Access database. For generating your schemas, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) assumes that the HL7 V2.2 data types are valid, and uses this information to build the schemas. Depending on the usage in the schema, an appropriate data type must be used, meaning that the data type must be replaced with CK, CQ, CE, ST^SI, and so on.  
  
## See Also  
 [Data Types](../../adapters-and-accelerators/accelerator-hl7/data-types.md)   
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)