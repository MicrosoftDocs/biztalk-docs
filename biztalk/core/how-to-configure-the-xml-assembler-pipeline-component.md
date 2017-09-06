---
title: "How to Configure the XML Assembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML Assembler [pipeline component], configuring"
  - "messages, XML documents"
  - "messages, envelopes"
  - "configuring, pipeline components"
  - "pipeline components, XML Assembler"
ms.assetid: 6d883819-a1d4-4ad0-b08f-fcd7583134d6
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the XML Assembler Pipeline Component
The XML Assembler pipeline component is used to wrap the XML documents into the XML envelopes before sending a message from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### To configure the properties for the XML Assembler pipeline component  
  
1.  Drag the XML Assembler pipeline component into the Assemble stage of a send pipeline.  
  
2.  In the Properties window, in the **Pipeline Component Properties** section, do the following.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Add processing instructions**|**Append**: Value of **Add processing instructions text** should append to pre-existing processing instructions in the message.<br /><br /> **Create New:** Value of **Add processing instructions text** entered in the field should overwrite or replace any pre-existing processing instructions in the message.<br /><br /> If **Create New** is selected, the **Add processing instructions text** must contain valid processing instructions.<br /><br /> **Ignore**: If processing instructions text exists in the message, it is removed.<br /><br /> Default value: **Append**|  
    |**Add processing instructions text**|Specifies the XML processing instructions to add to the beginning of the target XML document. **Note:**  Processing instruction text should conform to the W3C XML processing instruction standards. <br /><br /> Default value: None|  
    |**Add XML declarations**|When **True**, adds an XML declaration similar to the following to the outgoing document: `<?xml version='1.0' encoding='UTF-8'>`. Encoding is determined by the target document encoding set at run time.<br /><br /> Default value: **True**|  
    |**Document schemas**|Indicates the namespace and typename of the schema or schemas to be applied to the document. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md). **Note:**  You may receive a "Two or more of the selected schema share the same target namespace" error if you specify two or more schemas for the **Document schemas** property. <br /><br /> Default value: Empty collection|  
    |**Envelope schemas**|Indicates the namespace and typename of the schema or schemas that will be applied to the envelope. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md). **Note:**  You may receive a "Two or more of the selected schema share the same target namespace" error if you specify two or more schemas for the **Envelope schemas** property. <br /><br /> Default value: Empty collection|  
    |**Preserve byte order mark**|Specifies whether to add a byte order mark (BOM) to the documents produced by the assembler component.<br /><br /> Default value: **True**|  
    |**Processing instruction scope**|Specifies whether the processing instruction is defined on the outermost envelope or at the document level.<br /><br /> Default value: **Document**|  
    |**Target charset**|Specifies the character set used to encode outgoing messages.<br /><br /> Default value: None|  
  
## See Also  
 [XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [XML and Flat File Property Schema and Properties](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)