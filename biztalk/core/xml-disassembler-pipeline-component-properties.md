---
title: "XML Disassembler Pipeline Component Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.BizTalk.Component.XmlDasmComp"
ms.assetid: bec76e08-3a06-43ff-b22f-3c71f00f7783
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML Disassembler Pipeline Component Properties
Use the XML disassembler pipeline component to do the following:  
  
-   Remove envelopes.  
  
-   Disassemble the interchange.  
  
-   Raise promoted content properties from the interchange and individual documents levels to the message context.  
  
 The XML disassembler pipeline component is intended for use in the Disassemble stage of a Receive pipeline.  
  
 The properties of the XML disassembler pipeline component can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable XML disassembler pipeline component properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Allow unrecognized message**|Indicate whether to allow messages that do not have a recognized message type to be passed through the disassembler.<br /><br /> Default Value: False|  
|**Document schemas**|Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Default value: Empty collection (Collection)|  
|**Envelope schemas**|Indicate the namespace and typename of the schema or schemas to be applied to the envelope. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Default value: Empty collection (Collection)|  
|**Recoverable interchange processing**|Indicate whether to process messages within an interchange individually. For more information, see [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md).<br /><br /> Default Value: False|  
|**Validate document structure**|Perform a validation of the incoming message against document and optionally envelope schemas, when set to True.<br /><br /> Default Value: False|  
  
## See Also  
 [Using Pipeline Designer](../core/using-pipeline-designer.md)   
 [XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md)   
 [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)   
 [XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md)   
 [XML and Flat File Property Schema and Properties](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [XML Information Set Elements in the XML Disassembler Pipeline Component](../core/xml-information-set-elements-in-the-xml-disassembler-pipeline-component.md)   
 [Unrecognized Messages in the XML Disassembler Pipeline Component](../core/unrecognized-messages-in-the-xml-disassembler-pipeline-component.md)   
 [Document Validation in the XML Disassembler Pipeline Component](../core/document-validation-in-the-xml-disassembler-pipeline-component.md)   
 [Document Structure Enforcement in the XML Disassembler Pipeline Component](../core/document-structure-enforcement-in-the-xml-disassembler-pipeline-component.md)   
 [Character Encoding in XML Disassembler Pipeline Component](../core/character-encoding-in-xml-disassembler-pipeline-component.md)