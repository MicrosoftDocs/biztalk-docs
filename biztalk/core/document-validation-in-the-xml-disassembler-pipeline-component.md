---
description: "Learn more about: Document Validation in the XML Disassembler Pipeline Component"
title: "Document Validation in the XML Disassembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Validate Document Structure property"
  - "pipeline components, XML Disassembler"
  - "XML Disassembler [pipeline component], document validation"
  - "XML Disassembler [pipeline component], warnings"
ms.assetid: feb25033-46d3-48ed-8e1f-0cd123e94149
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Document Validation in the XML Disassembler Pipeline Component
By default, the XML Disassembler does not validate XML documents against a schema. However, you can configure the XML Disassembler to validate an XML document by setting the **Validate Document Structure** property.  
  
> [!CAUTION]
>  If a field for promotion is declared with a simple data type but contains complex data, the property promotion will cause unpredictable results. To avoid this scenario, configure the XML Disassembler to perform document validation by setting the **Validate Document Structure** property to **True**.  
  
## See Also  
 [XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md)   
 [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)
