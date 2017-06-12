---
title: "XML Assembler Pipeline Component Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.BizTalk.Component.XmlAsmComp"
ms.assetid: a5095838-bb3c-4da9-9f83-ff2f4f9e0465
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML Assembler Pipeline Component Properties
Use the XML assembler pipeline component to transfer properties from the message context back into envelopes and documents.  
  
 The XML assembler pipeline component is intended for use in the Assemble stage of the Send pipeline.  
  
 The properties of the XML assembler pipeline component can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable XML assembler pipeline component properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Add processing instructions**|Specify how XML processing instructions are handled in the XML instance document.<br /><br /> Append: The value of **Add Processing Instructions Text** should append to the pre-existing processing instructions in the message.<br /><br /> Create New: Thevalue of **Add Processing Instructions Text** entered in the field should overwrite or replace any pre-existing processing instructions in the message.<br /><br /> If **Create New** is selected, then **Add Processing Instructions Text**must contain valid processing instructions.<br /><br /> **Ignore**: If processing instructions text exists in the message, it is removed.<br /><br /> Default Value: Append|  
|**Add processing instructions text**|Specify what XML processing instructions to add to the beginning of the target XML document. **Note:**  Processing instruction text should conform to the W3C XML processing instruction standards. <br /><br /> Default Value: None|  
|**Add XML declaration**|Add an XML declaration similar to the following to the outgoing document `<?xml version='1.0' encoding='UTF-8'>`, when set to True. Encoding is determined by the target document encoding set at runtime.<br /><br /> Default Value: True|  
|**Document schemas**|Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Default value: Empty collection (Collection)|  
|**Envelope schemas**|Indicate the namespace and typename of the schema or schemas that will be applied to the envelope. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Default value: Empty collection (Collection)|  
|**Preserve byte order mark**|Specifies whether to add a byte order mark (BOM) to the documents produced by the assembler component.<br /><br /> Default value: True|  
|**Processing instruction scope**|Specifies whether the processing instruction is defined on the outermost envelope or at the document level.<br /><br /> Default value: Document|  
|**Target charset**|Identify the character set used for the encoding of outgoing messages.<br /><br /> Default value: (None)|  
  
## See Also  
 [Using Pipeline Designer](../core/using-pipeline-designer.md)   
 [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [XML Information Set Elements in the XML Assembler Pipeline Component](../core/xml-information-set-elements-in-the-xml-assembler-pipeline-component.md)   
 [Character Encoding in the XML Assembler Pipeline Component](../core/character-encoding-in-the-xml-assembler-pipeline-component.md)   
 [Unrecognized Messages in the XML Assembler Pipeline Component](../core/unrecognized-messages-in-the-xml-assembler-pipeline-component.md)   
 [Document Structure Enforcement in the XML Assembler Pipeline Component](../core/document-structure-enforcement-in-the-xml-assembler-pipeline-component.md)   
 [Processing Instructions in the XML Assembler Pipeline Component](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)