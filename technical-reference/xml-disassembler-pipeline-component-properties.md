---
title: XML Disassembler Pipeline Component Properties
TOCTitle: XML Disassembler Pipeline Component Properties
ms:assetid: bec76e08-3a06-43ff-b22f-3c71f00f7783
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578415(v=BTS.80)
ms:contentKeyID: 51531004
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- Microsoft.BizTalk.Component.XmlDasmComp
---

# XML Disassembler Pipeline Component Properties

 

Use the XML disassembler pipeline component to do the following:

  - Remove envelopes.

  - Disassemble the interchange.

  - Raise promoted content properties from the interchange and individual documents levels to the message context.

The XML disassembler pipeline component is intended for use in the Disassemble stage of a Receive pipeline.

The properties of the XML disassembler pipeline component can be set in the Properties window of Microsoft Visual Studio. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable XML disassembler pipeline component properties.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Allow unrecognized message</strong></td>
<td>Indicate whether to allow messages that do not have a recognized message type to be passed through the disassembler.<br />
<br />
Default Value: False</td>
</tr>
<tr class="even">
<td><strong>Document schemas</strong></td>
<td>Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see <a href="https://msdn.microsoft.com/library/aa559127(v=bts.80)">How to Use the Schema Collection Property Editor</a>.<br />
<br />
Default value: Empty collection (Collection)</td>
</tr>
<tr class="odd">
<td><strong>Envelope schemas</strong></td>
<td>Indicate the namespace and typename of the schema or schemas to be applied to the envelope. For more information, see <a href="https://msdn.microsoft.com/library/aa559127(v=bts.80)">How to Use the Schema Collection Property Editor</a>.<br />
<br />
Default value: Empty collection (Collection)</td>
</tr>
<tr class="even">
<td><strong>Recoverable interchange processing</strong></td>
<td>Indicate whether to process messages within an interchange individually. For more information, see <a href="https://msdn.microsoft.com/library/aa578714(v=bts.80)">Recoverable Interchange Processing</a>.<br />
<br />
Default Value: False</td>
</tr>
<tr class="odd">
<td><strong>Validate document structure</strong></td>
<td>Perform a validation of the incoming message against document and optionally envelope schemas, when set to True.<br />
<br />
Default Value: False</td>
</tr>
</tbody>
</table>


## See Also

[Using Pipeline Designer](https://msdn.microsoft.com/library/aa578392\(v=bts.80\))  
[XML Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa561814\(v=bts.80\))  
[How to Configure the XML Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa577393\(v=bts.80\))  
[XML Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa561814\(v=bts.80\))  
[XML and Flat File Property Schema and Properties](https://msdn.microsoft.com/library/aa559096\(v=bts.80\))  
[XML Information Set Elements in the XML Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa548044\(v=bts.80\))  
[Unrecognized Messages in the XML Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa560317\(v=bts.80\))  
[Document Validation in the XML Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa562154\(v=bts.80\))  
[Document Structure Enforcement in the XML Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa578016\(v=bts.80\))  
[Character Encoding in XML Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa559602\(v=bts.80\))

