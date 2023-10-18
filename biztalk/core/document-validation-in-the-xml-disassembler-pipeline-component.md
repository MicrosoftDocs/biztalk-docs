---
description: "Learn more about: Document Validation in the XML Disassembler Pipeline Component"
title: "Document Validation in the XML Disassembler Pipeline Component"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Document Validation in the XML Disassembler Pipeline Component
By default, the XML Disassembler does not validate XML documents against a schema. However, you can configure the XML Disassembler to validate an XML document by setting the **Validate Document Structure** property.  
  
> [!CAUTION]
>  If a field for promotion is declared with a simple data type but contains complex data, the property promotion will cause unpredictable results. To avoid this scenario, configure the XML Disassembler to perform document validation by setting the **Validate Document Structure** property to **True**.  
  
## See Also  
 [XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md)   
 [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)
