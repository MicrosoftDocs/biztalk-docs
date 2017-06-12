---
title: "Vocabulary | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, vocabulary"
  - "vocabularies"
ms.assetid: c5df05dd-4af8-4e48-8509-e692b04adf3c
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Vocabulary
HL7 Version 2 provides some support for vocabularies for coded elements, but for the most part, provides a structure that transmits codes drawn from local coding systems.  
  
 In HL7 Version 2, a segment table links all coded fields. The segment table includes the identifier of the table that the field uses. There are three types of tables: HL7 defined, externally defined, and user-defined. In some cases, the standard supplies example values for a user-defined table. You should treat these as the HL7 standard has labeled them.  
  
 In new versions, you cannot remove codes from HL7 defined tables, but you can add new codes. You can change user-defined tables at will.  
  
 The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:  
  
-   You can use all of the HL7 defined tables.  
  
-   You can import and use externally defined code sets such as ICD9 and LOINC.  
  
-   You can provide the values for user-defined tables.  
  
-   In cases where systems are supporting different sets of codes, you can set up mappings that allow disparate code sets to interoperate. If necessary, you can define multiple instances of a single user-defined table to go along with the intermediary mapping.  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)