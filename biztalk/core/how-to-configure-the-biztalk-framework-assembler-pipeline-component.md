---
description: "Learn more about: Configure the BizTalk Framework Assembler Pipeline Component"
title: "Configure the Framework Assembler Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fd51047-b9dd-4b98-a968-45d69148664e
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the BizTalk Framework Assembler Pipeline Component
  
1.  Drag the BizTalk Framework Assembler pipeline component into the Assemble stage of the send pipeline.  
  
2.  In the Properties window, in the **Pipeline Component Properties** section, set the following property values.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Add processing instructions text**|Allows assembled XML documents to contain processing instructions as a value of this property. This also allows documents to contain instructions for applications. **Note:**  Processing instruction text should conform to the W3C XML processing instruction standards. <br /><br /> Default value: Append|  
    |**Add XML declaration**|Adds an XML declaration to an outgoing message. When true, the following XML declaration is added to the outgoing message: `<?xml version='1.0' encoding='UTF8'>`. The encoding specified depends on the encoding used by the BizTalk Framework Assembler, which honors the specific run-time properties carrying the encoding information.<br /><br /> Default value: **True**|  
    |**Delivery receipt address**|Specifies the address to which the delivery receipt for the BizTalk Framework document should be sent. **Warning:**  When using the BizTalk Framework Assembler with acknowledgements enabled, there is a chance that acknowledgement processing can become backlogged resulting in a deadlock. The deadlock occurs when multiple acknowledgements are processed in separate batches for a single message. To avoid this problem you should configure the batch size to 1 for the delivery receipt address port location entered.|  
    |**Delivery receipt address type**|Specifies the type of address to which the delivery receipt for the BizTalk Framework document should be sent.<br /><br /> Default value: biz: **Note:**  The biz: prefix was used to signify organization identifiers for the source and destination endpoints in BizTalk Server, and for interoperability with those systems. The prefix is provided as a default. For example, type = "biz:OrganizationName", (src&#124;dest) = "Party1".|  
    |**Delivery receipt send by time**|Specifies the time (in minutes) by which the delivery receipt for the BizTalk Framework document must be received.<br /><br /> Default value: 30|  
    |**Destination address**|Specifies the destination address.<br /><br /> Default value: None|  
    |**Destination address type**|Specifies the destination address type.<br /><br /> Default value: biz: **Note:**  The biz: prefix was used to signify organization identifiers for the source and destination endpoints in BizTalk Server, and for interoperability with those systems. The prefix is provided as a default. For example, type = "biz:OrganizationName", (src&#124;dest) = "Party1".|  
    |**Document schemas**|Indicates the namespace and typename of the schema or schemas to be applied to the document. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md). **Note:**  You may receive a "Two or more of the selected schema share the same target namespace" error if you specify two or more schemas for the **Document schemas** property. <br /><br /> Default value: Empty collection|  
    |**Document topic**|Identifies a URI reference that uniquely identifies the overall purpose of the BizTalk Framework document.<br /><br /> Default value: None|  
    |**Envelope schemas**|Indicates the namespace and typename of the schema or schemas that will be applied to the envelope. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md). **Note:**  You may receive a "Two or more of the selected schema share the same target namespace" error if you specify two or more schemas for the **Envelope schemas** property. <br /><br /> Default value: BTF2Schemas.btf2_envelope|  
    |**Generate delivery request receipt**|Indicates whether the delivery receipt request for the BizTalk Framework document should be generated. This is used to enable reliable messaging for the BizTalk Framework.<br /><br /> Default value: **True**|  
    |**Message time to live (in minutes)**|Specifies the amount of time (in minutes) that the message is valid.<br /><br /> Default value: 30|  
    |**Processing instructions**|Specifies how XML processing instructions are handled in the XML instance document.<br /><br /> **Append**: The value of **Add processing instructions text** should append to pre-existing processing instructions in the message.<br /><br /> **Create New**: The value of **Add processing instructions text** entered in the field should overwrite or replace any pre-existing processing instructions in the message.<br /><br /> If **Create New** is selected, **Add processing instructions text** must contain valid processing instructions.<br /><br /> **Ignore**: If processing instructions text exists in the message, it is removed.<br /><br /> Default value: **Append**|  
    |**Source address**|Specifies the source address.<br /><br /> Default value: None|  
    |**Source address type**|Specifies the source address type.<br /><br /> Default value: biz: **Note:**  The biz: prefix was used to signify organization identifiers for the source and destination endpoints in BizTalk Server, and for interoperability with those systems. The prefix is provided as a default. For example, type = "biz:OrganizationName", (src&#124;dest) = "Party1".|  
    |**Target charset**|Specifies the target character set used for encoding of outgoing messages.<br /><br /> Default value: None|  
  
## See Also  
 [BizTalk Framework Assembler Pipeline Component](../core/biztalk-framework-assembler-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
