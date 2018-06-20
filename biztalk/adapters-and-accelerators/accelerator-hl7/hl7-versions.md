---
title: "HL7 Versions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HL7, standards"
  - "HL7, versions"
ms.assetid: 47299c6f-55c3-4434-8170-5ad73fe9a84c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HL7 Versions
HL7 Version 2 is a family of closely related standards rather than a single standard. The HL7 organization has designed these standards to be upwards compatible through the application of the HL7 inter-version compatibility rules. These rules guarantee that, within the confines of Version 2, an interface defined under the rules of an HL7 version will still function within the definition of successor versions. So that a receiving system will be able to accept messages from later versions without breaking its implementation and a sending system will be able to continue to send messages to receivers who support later versions.  
  
 It is important to note that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]):  
  
- Supports all live HL7 versions from Version 2.1 through Version 2.5  
  
- Provides the functionality needed to map between HL7 versions, and enables the interoperability of multiple versions at a single site  
  
- Supports localization by supporting Z segments, and enables mapping between alternate interpretations or uses of the standard messages  
  
  It is important to note the difference between the versions of the messaging standard:  
  
- Version 1 functioned as a proof of concept  
  
- Version 2 provides a collection of message specifications to support message exchange between applications  
  
- Version 3 will provide a model-based integrated set of specifications to support a range of interoperability needs  
  
  In essence, Version 2 focuses on a pragmatic approach to providing users with the specifications they need to carry out specified tasks, while Version 3 focuses on assuring consistency and long-term extensibility for the body of message specifications taken as a whole.  
  
  The Clinical Document Architecture provides a significant extension to the HL7 standard by introducing standards for the representation of clinical documents using XML.  
  
  The following table shows the HL7 standard development progression.  
  
|Event|Year|Details|  
|-----------|----------|-------------|  
|HL7 Founded|1987|The first meeting, in Stanford, CA, included 12 attendees.|  
|V1.0|1987|Draft presented to HL7 plenary meeting.|  
|V2.0|1988|Draft presented to HL7 plenary meeting.|  
|V2.1 published|1990|The first widely implemented version|  
|V2.2 published|1994||  
|V.2.3 published|1997|ANSI approved|  
|V2.3.1 published|1999|ANSI approved|  
|V2.4 published|2000|ANSI approved|  
|Clinical Document Architecture|2000|ANSI approved|  
|V2.5 published|2003|Completed approval within HL7, submitted to ANSI for approval.|  
|V3.0 in progress|2003||  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [Message Modes](../../adapters-and-accelerators/accelerator-hl7/message-modes.md)   
 [HL7 Messaging](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)