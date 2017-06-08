---
title: "Configure Pipeline Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.pipeline.configure"
ms.assetid: 1eff5976-417a-4ed2-8688-ad12d6f51eaf
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure Pipeline Dialog Box
Use the **Configure Pipeline** dialog box to edit configurable pipeline properties. The properties of a specific **Configure Pipeline** dialog box will depend on whether the pipeline is for sending or receiving, and what stages and components within those stages that the specific pipeline contains. Changes that you make are applied to the per-instance pipeline property, and will overwrite the properties set at design time.  
  
## Receive Pipeline  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**AllowUnrecognizedMessage**|Indicates whether to allow messages that do not have a recognized message type to be passed through the disassembler.<br /><br /> Default value: **False**|  
|**DocumentSpecNames**|Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see Using the Schema Collection Property Editor. To specify more than one schema, separate them using the &#124; (pipe) character. For example:<br /><br /> Microsoft.Samples.BizTalk.EnvelopeProcessing.PO1&#124;Microsoft.Samples.BizTalk.EnvelopeProcessing.PO2&#124;Microsoft.Samples.BizTalk.EnvelopeProcessing.PO3<br /><br /> Default value: Empty collection (Collection)|  
|**EnvelopeSpecNames**|Indicate the namespace and typename of the schema or schemas to be applied to the envelope. For more information, see Using the Schema Collection Property Editor. To specify more than one schema, separate them using the &#124; (pipe) character. For example:<br /><br /> Samples.BizTalk.EnvelopeProcessing.Envelope1&#124;Microsoft.Samples.BizTalk.EnvelopeProcessing.Envelope2<br /><br /> Default value: (Collection), **BTF2Schemas.btf2_envelope**|  
|**RecoverableInterchangeProcess**|This property is used to control the interchange processing mode. When the disassembler component of a receive pipeline is configured to perform recoverable interchange processing, the messages contained in an interchange are extracted independently of each other.<br /><br /> Messages that are successfully extracted are propagated further down the receive pipeline. Messages that are identified within an interchange but are not successfully extracted are placed in the Suspended queue.|  
|**ValidateDocument**|Perform a validation of the incoming message to the disassembler, including validating the envelope(s), when set to True.<br /><br /> Default value: **False** **Note:**  You must specify a document schema (using the **Document schema** property) and have it deployed if you want to validate the document structure. If you fail to specify a document schema, you will receive a runtime error.|  
|**AllowByCertName**|Indicates whether to enable party resolution based on the thumbprint of the signature certificate from the party from where the messages are received.|  
|**AllowBySID**|Set to **True** if you want to enable party resolution based on the security identifier (SID) of the sender account.<br /><br /> If both properties are set to **True**, the AllowByCertName property takes precedence over the AllowBySID property, meaning that if both the certificate and the SID are available, the certificate subject is used.<br /><br /> If the party cannot be resolved by using the certificate subject, the component does not fall back to the AllowByCertName property, and the default value (s-1-5-7) is stamped for BTS.SourcePartyID.<br /><br /> Default value: **True**|  
  
## Send Pipeline  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Pre-assemble**|Specify the component properties required to perform any action on the message before the message is serialized.|  
|**Assemble**|Specify the component properties for assembly, serialization, and format conversion of outbound messages. The list of properties and descriptions follows this table.|  
|**Encode**|Specify the component properties required to encode or encrypt the message.|  
  
 **Available component properties**  
  
|Property|Description|  
|--------------|-----------------|  
|**AddXMLDeclaration**|Specifies whether an XML declaration should be added to an outgoing document.|  
|**DocumentSpecName**|The schema for XML components to use for parsing or serializing documents.<br /><br /> Schemas specified in this property should have unique target namespaces. If any of the schemas have the same namespace, the validation of the document instances may not work as expected. If schemas must have the same namespace, you should either create a separate pipeline for each schema and specify one schema per XML Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the XML Disassembler pipeline component.|  
|**EnvelopeDocSpecName**|The envelope specification for XML components to use for parsing or serializing documents.<br /><br /> Schemas specified in this property should have unique target namespaces. If any of the schemas have the same namespace, the validation of the document instances may not work as expected. If schemas must have the same namespace, you should either create a separate pipeline for each schema and specify one schema per each XML Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the XML Disassembler pipeline component.|  
|**PreserveBom**|Specifies whether to preserve the byte order mark (BOM). BOM is a byte sequence at the beginning of a stream or file that indicates the encoding of the stream or file.|  
|**ProcessingInstructionOption**|Specifies how processing instructions are added to outgoing documents. For more information about the ProcessingInstructionOption, see [Processing Instructions in the XML Assembler Pipeline Component](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md).|  
|**ProcessingInstructionsScope**|Processing instruction scope indicates where processing instructions are inserted into the assembled XML document stream, either at the document level or at the envelope level.|  
|**TargetCharset**|The character set for XML components to use for encoding output messages. If you set this property, BizTalk Server converts the outbound documents to the specified character set regardless of the original one. Examples of valid character sets you can specify for this property include UCS-2 and UTF-16. If you do not set a target character set, XML uses the UTF-8 protocol and flat files use the code page specified in the flat file schema.|  
|**XmlAsmProcessingInstructions**|Provides information to the application that processes an XML document. Such information may include instructions about how to process the document, how to display it, and so on. **Note:**  Processing instructions should conform to the W3C XML processing instruction standards.|  
  
## See Also  
 [About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md)   
 [How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md)   
 [How to Configure Tracking for a Pipeline](../core/how-to-configure-tracking-for-a-pipeline.md)   
 [Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md)   
 [Receive Pipelines](../core/receive-pipelines.md)   
 [Send Pipelines](../core/send-pipelines.md)   
 [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)