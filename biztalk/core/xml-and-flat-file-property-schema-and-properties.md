---
title: "XML and Flat File Property Schema and Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d917b82-62c6-489f-99a9-97e429b6f7c0
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML and Flat File Property Schema and Properties
The **http://schemas.microsoft.com/BizTalk/2003/xmlnorm-properties** namespace contains properties you can use to configure Flat File Assembler and Flat File Disassembler pipeline components. The properties are described in the following table.  

## Properties list

|Property|Type|Description|  
|--------------|----------|-----------------|  
|**FlatFileHeaderDocument**|xs:string|The header of an incoming flat file document can be stored with this property.|  
|**AllowUnrecognizedMessage**|xs:Boolean|Specifies whether unrecognized messages should be processed by XML components.|  
|**ProcessingInstruction**|xs:string|Processing instruction text for outgoing documents.|  
|**DocumentSpecName**|xs:string|The schema for XML components to use for parsing or serializing documents.<br /><br /> Schemas specified in this property should have unique target namespaces # root. If any of the schemas have the same namespace # root, the validation of the document instances may not work as expected. The namespace # root must be unique.  If schemas must have the same namespace # root, you should either create a separate pipeline for each schema and specify one schema per XML Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the XML Disassembler pipeline component.  This will also work if there is no target namespace.|  
|**EnvelopeSpecName**|xs:string|The envelope specification for XML components to use for parsing or serializing documents.<br /><br /> Schemas specified in this property should have unique target namespaces # root. If any of the schemas have the same namespace # root, the validation of the document instances may not work as expected. The namespace # root must be unique.  If schemas must have the same namespace # root, you should either create a separate pipeline for each schema and specify one schema per XML Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the XML Disassembler pipeline component.  This will also work if there is no target namespace.|  
|**TargetCharset**|xs:string|The character set for XML components to use for encoding output messages.|  
|**SourceCharset**|xs:string|The character set used to encode a document before being processed by the XML Disassembler.|  
|**ProcessingInstructionOption**|xs:int|Specifies how processing instructions are added to outgoing documents. For more information about the ProcessingInstructionOption, see [Processing Instructions in the XML Assembler Pipeline Component](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md).|  
|**AddXMLDeclaration**|xs:boolean|Specifies whether an XML declaration should be added to an outgoing document.|  
|**HeaderSpecName**|xs:string|Specifies a flat file document header.|  
|**TrailerSpecName**|xs:string|Specifies a flat file document trailer.|  
|**PromotePropertiesOnly**|xs:boolean|When set to **True**, the XML Disassembler component does not remove a message envelope or disassemble it. Only property promotion is performed.|  

## See Also  
- [Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)   
- [Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
- [Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
- [Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)   
- [Configure Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
- **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
