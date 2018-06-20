---
title: "Envelope Use in the XML Assembler and Disassembler Pipeline Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XMLNorm.EnvelopeSpecNames property"
  - "XML Disassembler [pipeline component], envelopes"
  - "envelopes, nesting"
  - "envelopes, XML Disassembler [pipeline component]"
  - "envelopes, XML Assembler [pipeline component]"
  - "XML Assembler [pipeline component], envelopes"
  - "Envelope Specification Names property"
ms.assetid: ccffd2f7-c7b1-4103-a914-ae9b4b19bee3
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Envelope Use in the XML Assembler and Disassembler Pipeline Components
An XML message can include zero or more envelopes. The following example shows an envelope (in bold) wrapping an XML document.  
  
```  
<ns1:document xmlns:ns1="http://myDocumentNamespaceURI.org">  
   <message>Hello</message>  
</ns1:document>  
  
```  
  
 Envelopes serve two purposes:  
  
- They can include field values to use for property promotion and demotion.  
  
   The XML Disassembler component promotes properties, and the XML Assembler component demotes properties. Property promotion and demotion can also occur in XML documents.  
  
- They can combine several XML documents into a single interchange.  
  
   Because a well-formed XML document can have only one root element, an envelope enables you to combine multiple XML documents to share one root element.  
  
  You can enforce the canonical form by specifying the envelope order by using the **Schema Collection Property Editor** dialog which is accessed by clicking the ellipses for the **Envelope schemas** design-time property in the XML Assembler. You can also use the **XMLNORM.EnvelopeSpecNames** message context property before the XML Assembler is run. The XML Assembler produces an enveloped document in canonical form.  
  
## Nesting envelopes  
 You can nest envelopes to form complex document structures where several enveloped XML documents can be combined into a larger interchange. The following example shows an interchange wrapped by two envelopes.  
  
```  
<envelope1>  
   <document1/>  
   <envelope2>  
      <document2/>  
      <document3/>  
   </envelope2>  
   <document4/>  
</envelope1>  
```  
  
 The preceding example illustrates a flexible form, which means that a document can be on the same hierarchy level as an envelope. After disassembling the enveloped document, four separate documents are created (document1, document2, and so on).  
  
## See Also  
 [Pipeline Components](../core/pipeline-components.md)