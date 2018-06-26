---
title: "Unrecognized Messages in the XML Assembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XMLNorm.AllowUnrecognizedMessage property"
  - "XML Assembler [pipeline component], unrecognized messages"
  - "pipeline components, XML Assembler"
ms.assetid: dd98512a-33a4-4b2e-977e-1b3a30747c6a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Unrecognized Messages in the XML Assembler Pipeline Component
The XML Assembler component treats a message as "unrecognized" if a message has:  
  
-   No body part.  
  
-   An empty body part.  
  
-   No data in the body part.  
  
-   No associated schema deployed.  
  
> [!NOTE]
>  Non-XML messages are always treated as unrecognized.  
  
 The manner in which the XML Assembler handles an unrecognized message is controlled by the **XMLNorm.AllowUnrecognizedMessage** message context property.  
  
 When **XMLNorm.AllowUnrecognizedMessage** is set to **True**, the XML Assembler handles XML documents as follows:  
  
- A message with no body part or with an empty body part or empty data in the body part passes unchanged through the assembler.  
  
- A document that does not have a deployed schema associated with it passes unchanged through the assembler.  
  
- A document with an associated deployed schema is processed by the assembler (regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process).  
  
  If **XMLNorm.AllowUnrecognizedMessage** is set to **False**, the XML Assembler handles XML documents as follows:  
  
- A message with no body part or with an empty body part or empty data in the body part is not processed. An error is reported and the message is suspended.  
  
- A message that does not have a deployed schema associated with it is not processed. An error is reported and the message is suspended.  
  
- A document with an associated deployed schema is processed by the assembler (regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process).  
  
- By default, the XML Assembler component does not allow unrecognized messages (that is, **XMLNorm.AllowUnrecognizedMessages** is considered **False** if it is not set on the message context).  
  
## See Also  
 [XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md)   
 [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)