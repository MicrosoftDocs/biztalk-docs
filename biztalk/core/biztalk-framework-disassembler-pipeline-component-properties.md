---
title: "BizTalk Framework Disassembler Pipeline Component Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.BizTalk.Component.BtfDasmComp"
ms.assetid: c88cca43-21aa-41c1-87de-9b030510920c
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Framework Disassembler Pipeline Component Properties
Use the BizTalk Framework disassembler pipeline component to save the message context, and create a new message context with the BizTalk Framework property that needs to be generated.  
  
 The BizTalk Framework disassembler pipeline component is intended for use in the Disassemble stage of a Receive pipeline.  
  
 The properties of the BizTalk Framework disassembler pipeline component can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable BizTalk Framework disassembler pipeline component properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Allow unrecognized message**|Indicate whether to allow messages that do not have a recognized schema to be passed through the disassembler.<br /><br /> Default value: False|  
|**Document schemas**|Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Default value: Empty collection (Collection)|  
|**Envelope schemas**|Indicate the namespace and typename of the schema or schemas to be applied to the envelope. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Default value: (Collection), BTF2Schemas.btf2_envelope|  
|**Validate document structure**|Perform a validation of the incoming message to the disassembler, including validating the envelope(s), when set to True.<br /><br /> Default value: False|  
  
## See Also  
 [Using Pipeline Designer](../core/using-pipeline-designer.md)   
 [Envelope Use in the XML Assembler and Disassembler Pipeline Components](../core/envelope-use-in-the-xml-assembler-and-disassembler-pipeline-components.md)   
 [BizTalk Framework Disassembler Pipeline Component](../core/biztalk-framework-disassembler-pipeline-component.md)   
 [BizTalk Framework Schema and Properties](../core/biztalk-framework-schema-and-properties.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)