---
title: "Using Dynamic Data Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dynamic data validation"
  - "validating, dynamic data"
ms.assetid: 8dac7f74-92a7-447c-97bf-b1f3ce39b614
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Dynamic Data Validation
An important part of dynamic data validation is validating message content against dynamic data, which includes validating the message format and the message content. A document schema, which [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server implements in an XSD file, defines and validates message formats. Business rules define message content, which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] validates through Business Rule Engine policies. Content validation can include confirmation that data in the message instance matches data that may change with relative frequency. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] implements this type of validation in a dynamic manner, so that you can update this data in a production environment, without having to recompile code or shut down services.  
  
## Validate and Expose Data  
 There are two steps in performing Dynamic Data Validation (DDV):  
  
- Expose the data.  
  
- Apply validation rules using that data.  
  
  DDV provides the following support for storing, exposing, and caching dynamic data:  
  
- The Business Rule Engine or Message Class performs validation.  
  
- The Business Rule Engine exposes data through the Database table column vocabulary. The Business Rule Engine validates this dynamic data against messages by implementing a rule set that runs from a pipeline or orchestration.  
  
- Existing SQL interfaces, such as SQL Enterprise Manager and Query Analyzer, expose dynamic data that is passive at design time.  
  
- The Business Rule Engine database table column vocabulary definition exposes dynamic data at run time.  
  
- The Business Rule Engine exposes message instance data at run time.  
  
- A Business Rules Engine XML document vocabulary definition exposes message instance data at design time.  
  
- You can compose rules at design time in the Business Rule Composer user interface or directly in Business Rules Language (BRL) XML in a text editor.  
  
  For more information about business rules and the Business Rule Engine, see "Developing with Business Rules" in BizTalk Server Help.  
  
## Extending DDV  
 If you change HL7-based cross-field validation or data type validation, you must note two things:  
  
-   If you modify an existing rule, you do not need to redeploy.  
  
-   If you create or delete a new rule that a pipeline component affects, then you must recompile.  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)