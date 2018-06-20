---
title: "XML Disassembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML Disassembler [pipeline component], about XML Disassembler"
  - "pipeline components, XML Disassembler"
  - "XML Disassembler [pipeline component]"
ms.assetid: ef39b695-6ae7-401d-be1e-b066048c34e9
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML Disassembler Pipeline Component
The XML Disassembler pipeline component combines XML parsing and disassembling into one component. Its primary functions are:  
  
- Removing envelopes.  
  
- Disassembling the interchange.  
  
- Promoting the content properties from interchange and individual document levels on to the message context.  
  
  The following actions occur in the XML Disassembler component after receiving an envelope:  
  
1. The disassembler parses the envelope by using the envelope schemas statically associated with the component at design time or dynamically by determining envelope schemas from the message type at run time. The schema is used to verify the structure of the envelope during envelope parsing. If envelope structure is not defined, it is found recursively by using the root node's namespace and base name to look up the schemas.  
  
2. The disassembler component parses each document within the envelope. For each document, the BizTalk message object is created with its own context where all the properties promoted from the envelope and from the document itself get copied. The component pulls the content properties from the envelope and message instances by using the predefined XPaths coded as annotations in the XSD schemas associated with the envelope and message. The envelope schemas as well as the individual document schemas are associated with the disassembler component in Pipeline Designer.  
  
   The XML Disassembler only processes data in the body part of the message. Thus, only properties from body part can be promoted. Datetime values from the fields associated with the promotable properties get converted to UTC when property promotion occurs. Non-body parts are copied to the output message unchanged.  
  
> [!NOTE]
>  The XML Disassembler pipeline component currently forces conversion of all datetime properties to UTC before they reach the message store. BizTalk Server uses an SQL datetime type internally, which does not have information about the time zone. If you generate a datetime property in an orchestration, and then try to use it for correlation with subsequent messages, it may not work correctly, because the XML Disassembler pipeline component will convert it on response into UTC, and Microsoft SQL Server will have no way to identify the original and response time fields as identical. Similarly, you may encounter discrepancies when viewing message event and service instance tracking data.  
  
 For information about configuring the XML Disassembler pipeline component, see [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md).  
  
## In This Section  
  
-   [XML Information Set Elements in the XML Disassembler Pipeline Component](../core/xml-information-set-elements-in-the-xml-disassembler-pipeline-component.md)  
  
-   [Unrecognized Messages in the XML Disassembler Pipeline Component](../core/unrecognized-messages-in-the-xml-disassembler-pipeline-component.md)  
  
-   [Document Validation in the XML Disassembler Pipeline Component](../core/document-validation-in-the-xml-disassembler-pipeline-component.md)  
  
-   [Document Structure Enforcement in the XML Disassembler Pipeline Component](../core/document-structure-enforcement-in-the-xml-disassembler-pipeline-component.md)  
  
-   [Character Encoding in XML Disassembler Pipeline Component](../core/character-encoding-in-xml-disassembler-pipeline-component.md)  
  
-   [Walkthrough: Using XML Envelopes (Basic)](../core/walkthrough-using-xml-envelopes-basic.md)