---
title: Configure Pipeline Dialog Box
TOCTitle: Configure Pipeline Dialog Box
ms:assetid: 1eff5976-417a-4ed2-8688-ad12d6f51eaf
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559126(v=BTS.80)
ms:contentKeyID: 51526699
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.pipeline.configure
---

# Configure Pipeline Dialog Box

 

Use the **Configure Pipeline** dialog box to edit configurable pipeline properties. The properties of a specific **Configure Pipeline** dialog box will depend on whether the pipeline is for sending or receiving, and what stages and components within those stages that the specific pipeline contains. Changes that you make are applied to the per-instance pipeline property, and will overwrite the properties set at design time.

## Receive Pipeline

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>AllowUnrecognizedMessage</strong></td>
<td>Indicates whether to allow messages that do not have a recognized message type to be passed through the disassembler.<br />
<br />
Default value: <strong>False</strong></td>
</tr>
<tr class="even">
<td><strong>DocumentSpecNames</strong></td>
<td>Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see Using the Schema Collection Property Editor. To specify more than one schema, separate them using the | (pipe) character. For example:<br />
<br />
Microsoft.Samples.BizTalk.EnvelopeProcessing.PO1|Microsoft.Samples.BizTalk.EnvelopeProcessing.PO2|Microsoft.Samples.BizTalk.EnvelopeProcessing.PO3<br />
<br />
Default value: Empty collection (Collection)</td>
</tr>
<tr class="odd">
<td><strong>EnvelopeSpecNames</strong></td>
<td>Indicate the namespace and typename of the schema or schemas to be applied to the envelope. For more information, see Using the Schema Collection Property Editor. To specify more than one schema, separate them using the | (pipe) character. For example:<br />
<br />
Samples.BizTalk.EnvelopeProcessing.Envelope1|Microsoft.Samples.BizTalk.EnvelopeProcessing.Envelope2<br />
<br />
Default value: (Collection), <strong>BTF2Schemas.btf2_envelope</strong></td>
</tr>
<tr class="even">
<td><strong>RecoverableInterchangeProcess</strong></td>
<td>This property is used to control the interchange processing mode. When the disassembler component of a receive pipeline is configured to perform recoverable interchange processing, the messages contained in an interchange are extracted independently of each other.<br />
<br />
Messages that are successfully extracted are propagated further down the receive pipeline. Messages that are identified within an interchange but are not successfully extracted are placed in the Suspended queue.</td>
</tr>
<tr class="odd">
<td><strong>ValidateDocument</strong></td>
<td>Perform a validation of the incoming message to the disassembler, including validating the envelope(s), when set to True.<br />
<br />
Default value: <strong>False</strong> <strong>Note:</strong> You must specify a document schema (using the <strong>Document schema</strong> property) and have it deployed if you want to validate the document structure. If you fail to specify a document schema, you will receive a runtime error.</td>
</tr>
<tr class="even">
<td><strong>AllowByCertName</strong></td>
<td>Indicates whether to enable party resolution based on the thumbprint of the signature certificate from the party from where the messages are received.</td>
</tr>
<tr class="odd">
<td><strong>AllowBySID</strong></td>
<td>Set to <strong>True</strong> if you want to enable party resolution based on the security identifier (SID) of the sender account.<br />
<br />
If both properties are set to <strong>True</strong>, the AllowByCertName property takes precedence over the AllowBySID property, meaning that if both the certificate and the SID are available, the certificate subject is used.<br />
<br />
If the party cannot be resolved by using the certificate subject, the component does not fall back to the AllowByCertName property, and the default value (s-1-5-7) is stamped for BTS.SourcePartyID.<br />
<br />
Default value: <strong>True</strong></td>
</tr>
</tbody>
</table>


## Send Pipeline

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Pre-assemble</strong></td>
<td>Specify the component properties required to perform any action on the message before the message is serialized.</td>
</tr>
<tr class="even">
<td><strong>Assemble</strong></td>
<td>Specify the component properties for assembly, serialization, and format conversion of outbound messages. The list of properties and descriptions follows this table.</td>
</tr>
<tr class="odd">
<td><strong>Encode</strong></td>
<td>Specify the component properties required to encode or encrypt the message.</td>
</tr>
</tbody>
</table>


**Available component properties**

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>AddXMLDeclaration</strong></td>
<td>Specifies whether an XML declaration should be added to an outgoing document.</td>
</tr>
<tr class="even">
<td><strong>DocumentSpecName</strong></td>
<td>The schema for XML components to use for parsing or serializing documents.<br />
<br />
Schemas specified in this property should have unique target namespaces. If any of the schemas have the same namespace, the validation of the document instances may not work as expected. If schemas must have the same namespace, you should either create a separate pipeline for each schema and specify one schema per XML Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the XML Disassembler pipeline component.</td>
</tr>
<tr class="odd">
<td><strong>EnvelopeDocSpecName</strong></td>
<td>The envelope specification for XML components to use for parsing or serializing documents.<br />
<br />
Schemas specified in this property should have unique target namespaces. If any of the schemas have the same namespace, the validation of the document instances may not work as expected. If schemas must have the same namespace, you should either create a separate pipeline for each schema and specify one schema per each XML Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the XML Disassembler pipeline component.</td>
</tr>
<tr class="even">
<td><strong>PreserveBom</strong></td>
<td>Specifies whether to preserve the byte order mark (BOM). BOM is a byte sequence at the beginning of a stream or file that indicates the encoding of the stream or file.</td>
</tr>
<tr class="odd">
<td><strong>ProcessingInstructionOption</strong></td>
<td>Specifies how processing instructions are added to outgoing documents. For more information about the ProcessingInstructionOption, see <a href="https://msdn.microsoft.com/en-us/library/aa578687(v=bts.80)">Processing Instructions in the XML Assembler Pipeline Component</a>.</td>
</tr>
<tr class="even">
<td><strong>ProcessingInstructionsScope</strong></td>
<td>Processing instruction scope indicates where processing instructions are inserted into the assembled XML document stream, either at the document level or at the envelope level.</td>
</tr>
<tr class="odd">
<td><strong>TargetCharset</strong></td>
<td>The character set for XML components to use for encoding output messages. If you set this property, BizTalk Server converts the outbound documents to the specified character set regardless of the original one. Examples of valid character sets you can specify for this property include UCS-2 and UTF-16. If you do not set a target character set, XML uses the UTF-8 protocol and flat files use the code page specified in the flat file schema.</td>
</tr>
<tr class="even">
<td><strong>XmlAsmProcessingInstructions</strong></td>
<td>Provides information to the application that processes an XML document. Such information may include instructions about how to process the document, how to display it, and so on. <strong>Note:</strong> Processing instructions should conform to the W3C XML processing instruction standards.</td>
</tr>
</tbody>
</table>


## See Also

[About Pipelines, Stages, and Components](https://msdn.microsoft.com/library/aa577959\(v=bts.80\))  
[How to Create a New Pipeline](https://msdn.microsoft.com/library/aa578387\(v=bts.80\))  
[How to Configure Tracking for a Pipeline](https://msdn.microsoft.com/library/aa560101\(v=bts.80\))  
[Investigating Orchestration, Port, and Message Failures](https://msdn.microsoft.com/library/aa560126\(v=bts.80\))  
[Receive Pipelines](https://msdn.microsoft.com/library/aa561803\(v=bts.80\))  
[Send Pipelines](https://msdn.microsoft.com/library/aa547976\(v=bts.80\))  
[How to Configure the XML Assembler Pipeline Component](https://msdn.microsoft.com/library/aa560698\(v=bts.80\))  
[How to Configure the XML Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa577393\(v=bts.80\))

