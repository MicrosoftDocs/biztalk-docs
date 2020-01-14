---
title: "Configure the XML Disassembler Pipeline Component | Microsoft Docs"
ms.custom: "biztalk-2020"
ms.date: "01/13/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93dd9148-4ae4-4868-b85d-66eada354f58
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "dougeby"
---

# Configure the XML Disassembler Pipeline Component in BizTalk Server

The XML Disassembler pipeline component should be used in the Disassemble stage of a receive pipeline.  
  
## Configure the properties for the XML Disassembler pipeline component  
  
1.  Drag the XML Disassembler pipeline component into the Disassemble stage of a receive pipeline.  
  
2.  In the Properties window, in the **Pipeline Component Properties** section, do the following.  
  
    - **Allow unrecognized message**: Indicates whether to allow messages that do not have a recognized message type to be passed through the disassembler. Default value: **False**
    - **Document schemas**: Indicates the namespace and typename of the schema or schemas to be applied to the document. Default value: **Empty collection**

      For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).

      Schemas specified in this property should have unique target namespaces. If any of the schemas have the same namespace, the validation of the document instances may not work as expected. If schemas must have the same namespace, you should either create a separate pipeline for each schema and specify one schema per XML Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the XML Disassembler pipeline component.

    - **DtdProcessing**: Indicates whether to allow DTD processing within the pipeline. Default value: **empty**

      - When **Parse** or empty, DTD processing will be enabled.
      - When **Ignore**, DOCTYPE element in the incoming XML messages will be ignored and no DTD processing will occur.
      - When **Prohibit**, DTD processing will be disabled and any incoming XML messages that use DTD will get suspended.

      This setting applies to:

      - BizTalk Server 2020 and newer

    - **Envelope schemas**: Indicates the namespace and typename of the schema or schemas to be applied to the envelope. Default value: **Empty collection**

      For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).

      Schemas specified in this property should have unique target namespaces. If any of the schemas have the same namespace, the validation of the document instances may not work as expected. If schemas must have the same namespace, you should either create a separate pipeline for each schema and specify one schema per XML Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the XML Disassembler pipeline component.

    - **Recoverable Interchange Processing**: **False** indicates that entire interchange is disassembled as a unit (if any contained message fails, entire interchange is suspended).

      **True** indicates that messages within interchange are extracted individually by disassembler with possibility of some propagating through messaging pathway and others being suspended.

      For more information on recoverable interchange processing, see [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md).

    - **Validate document structure**: Default value: **False**

      When **True**, performs a validation of the incoming message against document and optionally envelope schemas. When **True**, you may receive a **Two or more of the selected schema share the same target namespace** error if you enter two or more schemas for the **Document schemas** or **Envelope schemas** properties.

      If a promoted property does not have a default or fixed value and this property is set to **False**, the property is not promoted.
  
## See Also

 [XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md)   
 [XML and Flat File Property Schema and Properties](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)
