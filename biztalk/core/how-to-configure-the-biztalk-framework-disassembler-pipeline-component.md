---
description: "Learn more about: How to Configure the BizTalk Framework Disassembler Pipeline Component"
title: "How to Configure the BizTalk Framework Disassembler Pipeline Component"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure the BizTalk Framework Disassembler Pipeline Component
The BizTalk Framework Disassembler pipeline component should be used in the Disassemble stage of a receive pipeline.  
  
### To configure the properties for the BizTalk Framework Disassembler pipeline component  
  
1.  Drag the BizTalk Framework Disassembler pipeline component into the Disassemble stage of a receive pipeline.  
  
2.  In the Properties window, in the **Pipeline Component Properties** section, do the following.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Allow unrecognized message**|Indicates whether to allow messages that do not have a recognized schema to be passed through the disassembler.<br /><br /> Default value: **False**|  
    |**Document schemas**|Indicates the namespace and typename of the schema or schemas to be applied to the document. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Schemas specified in this property should have unique target namespaces. If any of the schemas have the same namespace, the validation of the document instances may not work as expected. If schemas must have the same namespace, you should either create a separate pipeline for each schema and specify one schema per BizTalk Framework Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the BizTalk Framework Disassembler pipeline component.<br /><br /> Default value: Empty collection|  
    |**Envelope schemas**|Indicates the namespace and typename of the schema or schemas to be applied to the envelope. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Schemas specified in this property should have unique target namespaces. If any of the schemas have the same namespace, the validation of the document instances may not work as expected. If schemas must have the same namespace, you should either create a separate pipeline for each schema and specify one schema per BizTalk Framework Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the BizTalk Framework Disassembler pipeline component.<br /><br /> Default value: Empty collection|  
    |**Validate document structure**|When **True**, performs a validation of the incoming message to the disassembler, including the envelopes. **Note:**  When **True**, you may receive a "Two or more of the selected schema share the same target namespace" error if you specify two or more schemas for the **Document schemas** or **Envelope schemas** properties. <br /><br /> Default value: **False**|  
  
## See Also  
 [BizTalk Framework Disassembler Pipeline Component](../core/biztalk-framework-disassembler-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)
