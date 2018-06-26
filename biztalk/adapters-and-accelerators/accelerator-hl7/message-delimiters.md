---
title: "Message Delimiters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, events"
  - "messages, XML messages"
  - "events"
  - "delimiters"
  - "messages, delimiters"
  - "flat files"
  - "XML messages"
  - "messages, flat files"
ms.assetid: d25bf6db-5512-4c82-be0e-00da024c55d1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Delimiters
Message events defined by HL7 standards take the following form:  
  
- **Flat files**. Message events defined by HL7 versions 2.4 and earlier take the form of flat files.  
  
- **XML**. Message events defined by HL7 versions 2.XML and version 3 take the form of XML files.  
  
  Since the HL7 standard does not follow positional format, it uses delimiters to define the segment, field, component, and subcomponent levels of flat files. The following table lists the default delimiters used by HL7 flat files.  
  
|Delimiter|Value|Usage|  
|---------------|-----------|-----------|  
|Segment terminator|\<cr\>|A carriage return terminates a segment record. You cannot change this value.|  
|Field separator|&#124;|A pipe character separates two adjacent data fields within a segment. This character also separates the segment ID from the first data field in each segment.|  
|Component separator|^|A hat character separates adjacent components of data fields where allowed by the HL7 standard.|  
|Subcomponent separator|&|An ampersand character separates adjacent subcomponents of data fields where allowed by the HL7 standard. If there are no subcomponents, then you can omit this character.|  
|Repetition separator|~|A tilde character separates multiple occurrences of components or subcomponents in a field where allowed by the HL7 standard.|  
|Escape character|\|You use an escape character with any field that conforms to an ST, TX, or FT data type, or with the data (fourth) component of the ED data type. If no escape characters exist in a message, you can omit this character. However, you must include it if you use subcomponents in the message.|  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)