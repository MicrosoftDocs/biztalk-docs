---
title: "Types of Pipeline Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipelines, components"
ms.assetid: 9b493758-6b0f-4223-94bb-8f077ee735a9
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Types of Pipeline Components
Three types of pipeline components are included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]: general, assembling, and disassembling. Any of these three types can also implement probing functionality. This topic describes each type of component and the stages in which each component is generally used.  
  
## General  
 General components take one message, process the message, and produce zero or one message.  
  
 The MIME/SMIME Decoder, MIME/SMIME Encoder, Party Resolution, and Validator components are the included general components. You may need to create custom general components to compress the size of a message before sending, or to consume a message while waiting for additional information to process it.  
  
 General components should be placed in the Decode, Encode, Pre-assemble, ResolveParty, or Validate stages.  
  
 For information about developing general pipeline components, see [Developing a General Pipeline Component](../core/developing-a-general-pipeline-component.md).  
  
## Assembling  
 Assembling components have numerous responsibilities to prepare the message to be sent. First, the component converts the XML message to the appropriate XML or non-XML native format of the message, based on the type of assembler and properties set in the schema. In addition, assembling components assemble and wrap the message in an envelope, or add a header or trailer (or both) to the message. During assembly, some properties are moved from the message context to the body of the document or to the envelope.  
  
 The BizTalk Framework Assembler, Flat File Assembler, and XML Assembler components are the default assembling components.  
  
 Assembling components should be placed in the Assemble stage of send pipelines.  
  
 For information about developing assembling pipeline components, see [Developing an Assembling Pipeline Component](../core/developing-an-assembling-pipeline-component.md).  
  
## Disassembling  
 Disassembling components complete many tasks to prepare the message to be split up into individual documents according to envelope and document schemas for use within BizTalk Server. First, the disassembling component may convert non-XML messages into their XML representation, which is required for processing by BizTalk Server. Next, the message is disassembled into singular messages that can be sent to separate orchestrations. The message is disassembled by removing the envelope, splitting the message up into individual documents according to envelope and message schemas, and then moving properties from the envelope to the individual message contexts. Additionally, some properties may be promoted from the body of the message to the header. The promoted properties are determined by the schema.  
  
 The disassembling component must also set the message type property, which is used for routing messages appropriately. The message type property is the Namespace#RootElement of the message body. Other properties, such as the content type and character set are set as part of the context property.  
  
 The BizTalk Framework Disassembler, Flat File Disassembler, and XML Disassembler components are the default disassembling components included with BizTalk Server.  
  
 Disassembling components should be used in the Disassemble stage of receive pipelines.  
  
 For information about developing disassembling pipeline components, see [Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md).  
  
## Probing  
 A probing component checks the first portion of the message to see if it is in a format that the component understands. If the format is known, the whole message is given to this component for processing.  
  
 For information about developing probing pipeline components, see [Developing a Probing Pipeline Component](../core/developing-a-probing-pipeline-component.md).  
  
## See Also  
 [Types of Pipelines](../core/types-of-pipelines.md)   
 [Default Pipelines](../core/default-pipelines.md)   
 [Pipeline Templates](../core/pipeline-templates.md)   
 [Pipeline Components](../core/pipeline-components.md)   
 [About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md)