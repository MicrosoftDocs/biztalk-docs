---
title: "How to Configure the XML Assembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "01/13/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d883819-a1d4-4ad0-b08f-fcd7583134d6
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "dougeby"
---

# Configure the XML Assembler Pipeline Component in BizTalk Server

The XML Assembler pipeline component is used to wrap the XML documents into the XML envelopes before sending a message from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## Configure the properties for the XML Assembler pipeline component  
  
1.  Drag the XML Assembler pipeline component into the Assemble stage of a send pipeline.  
  
2.  In the Properties window, in the **Pipeline Component Properties** section, do the following.  
  
    - **Add processing instructions**: Your options:

      - **Append** (default): Value of **Add processing instructions text** should append to pre-existing processing instructions in the message.

      - **Create New:** Value of **Add processing instructions text** entered in the field should overwrite or replace any pre-existing processing instructions in the message.

        If **Create New** is selected, the **Add processing instructions text** must contain valid processing instructions.

      - **Ignore**: If processing instructions text exists in the message, it is removed.

    - **Add processing instructions text**: Specifies the XML processing instructions to add to the beginning of the target XML document. Default value: **None**

      Processing instruction text should conform to the W3C XML processing instruction standards.

    - **Add XML declarations**: When **True** (default), adds an XML declaration similar to the following to the outgoing document: `<?xml version='1.0' encoding='UTF-8'>`. Encoding is determined by the target document encoding set at run time.
    - **Document schemas**: Indicates the namespace and typename of the schema or schemas to be applied to the document. Default value: **Empty collection**

      For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).

      You may receive a **Two or more of the selected schema share the same target namespace** error if you enter two or more schemas for the **Document schemas** property.

    - **Envelope schemas**: Indicates the namespace and typename of the schema or schemas that will be applied to the envelope. Default value: **Empty collection**

      For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).

      You may receive a **Two or more of the selected schema share the same target namespace** error if you enter two or more schemas for the **Envelope schemas** property.
    - **Preserve byte order mark**: Specifies whether to add a byte order mark (BOM) to the documents produced by the assembler component. Default value: **True**
    - **Processing instruction scope**: Specifies whether the processing instruction is defined on the outermost envelope or at the document level. Default value: **Document**
    - **Target charset**: Specifies the character set used to encode outgoing messages. Default value: **None**
  
## See Also  

 [XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [XML and Flat File Property Schema and Properties](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
