---
title: "XML Information Set Elements in the XML Disassembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML Disassembler [pipeline component], information set"
  - "XML Disassembler [pipeline component], processing instructions"
  - "pipeline components, XML Disassembler"
ms.assetid: cc82344c-6c4b-4154-a662-0b7ae5caad30
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML Information Set Elements in the XML Disassembler Pipeline Component
The XML Disassembler handles XML information set elements as follows.  
  
|Element|Description|  
|-------------|-----------------|  
|comment|Comments are preserved in the document; however, any comments in XML envelopes are not preserved.|  
|CDATA|CDATA is preserved in the document. CDATA elements appearing outside of a document (for example, in an envelope) are not preserved.|  
|processing instructions|The XML Disassembler preserves processing instructions appearing in or before an XML document. Processing instructions appearing after an XML document or before or after an envelope are not preserved.|  
|XML declaration|The XML declaration element of any incoming XML message is removed.|  
  
## See Also  
 [XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md)   
 [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)