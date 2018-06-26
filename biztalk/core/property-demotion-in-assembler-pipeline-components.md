---
title: "Property Demotion in Assembler Pipeline Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML Assembler [pipeline component], properties"
  - "pipeline components, properties"
  - "BizTalk Framework Assembler [pipeline component], properties"
  - "XML Assembler [pipeline component], about XML Assembler"
  - "Flat File Assembler [pipeline component], properties"
ms.assetid: c5275638-d594-4b0d-a818-b7a9460b41a6
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Property Demotion in Assembler Pipeline Components
You can use property demotion to copy a property value from the message context into the message content or to its header or trailer. You accomplish property demotion by using an XPath expression specified in the document or in the header and trailer schema.  
  
 When writing datetime data from the context property into the resulting document, BizTalk Server assumes that all datetime data is in UTC format.  
  
 The format used to write properties into the data is determined by the XSD data type as shown in the following table.  
  
|Data type|Format|  
|---------------|------------|  
|xs:datetime|yyyy-MM-ddTHH:mm:ss.fffffffZ|  
|xs:date|yyyy-MM-ddZ|  
|xs:gDay|---ddZ|  
|xs:gMonth|--MM—Z|  
|xs:gMonthDay|--MM-ddZ|  
|xs:gYear|yyyyZ|  
|xs:gYearMonth|yyyy-MMZ|  
|xs:time|HH:mm:ss.fffffffZ|  
  
## Property Demotion and Envelopes  
 It is often useful to demote values from one or more of the system namespaces -- or one of your own namespaces -- when assembling files within an envelope. Some common scenarios include:  
  
- You want to include the original file name submitted to the system in outbound messages so back-end systems can track the origin of data.  
  
- You want to write data from the body message to the header. For example, for a purchase order it might be useful to write the ship to name to the envelope for down-stream systems.  
  
- You want to combine many different fields into the header without writing custom code. Property demotion in the Xml assembler or flat file assembler can do the job.  
  
  It is important to remember that the XML and flat file assembler components both allow you to specify which schema to use for the envelope and document body. You can choose the same schemas used in disassembly or create a new envelope schema with different fields.  
  
  For an example of these concepts, see [EnvelopeProcessing (BizTalk Server Sample)](../core/envelopeprocessing-biztalk-server-sample.md).  
  
## See Also  
 [Flat File Assembler Pipeline Component](../core/flat-file-assembler-pipeline-component.md)   
 [How to Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)