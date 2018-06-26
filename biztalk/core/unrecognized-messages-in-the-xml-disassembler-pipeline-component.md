---
title: "Unrecognized Messages in the XML Disassembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Allow Unrecognized Messages property"
  - "XMLNorm.AllowUnrecognizedMessage property"
  - "pipeline components, XML Disassembler"
  - "XML Disassembler [pipeline component], unrecognized messages"
ms.assetid: 5a6be3a8-0bac-426a-bf0b-5091191091de
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Unrecognized Messages in the XML Disassembler Pipeline Component
The XML Disassembler component may handle a message as "unrecognized" in the following cases:  
  
- An XML message is received with no body, an empty body, or empty data in the body.  
  
- An XML message is received but no schema is deployed for it.  
  
  An unrecognized message is handled based on the **Allow Unrecognized Messages** property (or on the **XMLNorm.AllowUnrecognizedMessage** property on the message context).  
  
  If **Allow Unrecognized Messages** is set to **True**, the following occurs:  
  
- A message with no body, an empty/null body, or with empty/null data in the body passes unchanged through the XML Disassembler.  
  
- An XML document with no associated deployed schema passes unchanged through the XML Disassembler.  
  
- An XML document that has a deployed schema associated with it is processed by the XML Disassembler regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process.  
  
  If **Allow Unrecognized Messages** is set to **False**, the following occurs:  
  
- A message with no body or an empty/null body or with empty/null data in the body is not passed through the XML Disassembler.  
  
- An XML document that does not have a deployed schema associated with it is not passed through the disassembler. An error is reported and the message is suspended, if possible.  
  
- An XML document that has a deployed schema associated with it is processed by the XML Disassembler regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process.  
  
  By default, the XML Disassembler does not allow unrecognized messages.  
  
> [!NOTE]
>  Non-XML messages are not processed by the XML Disassembler regardless of the **Allow Unrecognized Messages** property setting.  
  
## See Also  
 [XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md)   
 [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)