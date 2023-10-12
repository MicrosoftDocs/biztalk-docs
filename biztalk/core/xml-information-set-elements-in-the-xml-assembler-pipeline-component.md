---
description: "Learn more about: XML Information Set Elements in the XML Assembler Pipeline Component"
title: "XML Information Set Elements in the XML Assembler Pipeline Component"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# XML Information Set Elements in the XML Assembler Pipeline Component
The XML Assembler component handles XML information set elements as follows.  
  
|Element|Description|  
|-------------|-----------------|  
|comment|Comments are preserved between opening and closing XML tags in the document.|  
|CDATA|CDATA is preserved between opening and closing XML tags in the document. CDATA values are not used for property promotion or distinguished fields.|  
|processing instructions|Processing instructions located before the document XML tag are handled based on their value (for more information, see [Processing Instructions in the XML Assembler Pipeline Component](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)). Processing instructions between document open and close tags are preserved. Processing instructions after the closing XML tag are ignored, as are any instructions before, in, or after the envelope.|  
|XML declaration|The XML declaration string, such as `<?xml version='1.0'? encoding='UTF-8'>`, may be preserved by the XML Assembler pipeline component. This is controlled by the **Add XML declaration** property, or its equivalent on the message context, **XMLNorm.AddXMLDeclaration**.<br /><br /> If this option is set to **True** then the XML declaration will be added to the document. If the XML declaration already existed, it will be overwritten.<br /><br /> If this option is set to **False**, no XML declaration will be added and any existing XML declaration will be removed. The value of this property in the message context takes precedence over the value specified in Pipeline Designer.<br /><br /> Default value: **True** (the XML declaration is always added)|  
  
## See Also  
 [XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md)   
 [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
