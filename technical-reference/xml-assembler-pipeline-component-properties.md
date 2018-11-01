---
title: XML Assembler Pipeline Component Properties
TOCTitle: XML Assembler Pipeline Component Properties
ms:assetid: a5095838-bb3c-4da9-9f83-ff2f4f9e0465
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577876(v=BTS.80)
ms:contentKeyID: 51530268
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- Microsoft.BizTalk.Component.XmlAsmComp
---

# XML Assembler Pipeline Component Properties

 

Use the XML assembler pipeline component to transfer properties from the message context back into envelopes and documents.

The XML assembler pipeline component is intended for use in the Assemble stage of the Send pipeline.

The properties of the XML assembler pipeline component can be set in the Properties window of Microsoft Visual Studio. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable XML assembler pipeline component properties.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Add processing instructions</strong></td>
<td>Specify how XML processing instructions are handled in the XML instance document.<br />
<br />
Append: The value of <strong>Add Processing Instructions Text</strong> should append to the pre-existing processing instructions in the message.<br />
<br />
Create New: Thevalue of <strong>Add Processing Instructions Text</strong> entered in the field should overwrite or replace any pre-existing processing instructions in the message.<br />
<br />
If <strong>Create New</strong> is selected, then <strong>Add Processing Instructions Text</strong>must contain valid processing instructions.<br />
<br />
 <strong>Ignore</strong>: If processing instructions text exists in the message, it is removed.<br />
<br />
Default Value: Append</td>
</tr>
<tr class="even">
<td><strong>Add processing instructions text</strong></td>
<td>Specify what XML processing instructions to add to the beginning of the target XML document. <strong>Note:</strong> Processing instruction text should conform to the W3C XML processing instruction standards.<br />
<br />
Default Value: None</td>
</tr>
<tr class="odd">
<td><strong>Add XML declaration</strong></td>
<td>Add an XML declaration similar to the following to the outgoing document <code>&lt;?xml version='1.0' encoding='UTF-8'&gt;</code>, when set to True. Encoding is determined by the target document encoding set at runtime.<br />
<br />
Default Value: True</td>
</tr>
<tr class="even">
<td><strong>Document schemas</strong></td>
<td>Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see <a href="https://msdn.microsoft.com/en-us/library/aa559127(v=bts.80)">How to Use the Schema Collection Property Editor</a>.<br />
<br />
Default value: Empty collection (Collection)</td>
</tr>
<tr class="odd">
<td><strong>Envelope schemas</strong></td>
<td>Indicate the namespace and typename of the schema or schemas that will be applied to the envelope. For more information, see <a href="https://msdn.microsoft.com/en-us/library/aa559127(v=bts.80)">How to Use the Schema Collection Property Editor</a>.<br />
<br />
Default value: Empty collection (Collection)</td>
</tr>
<tr class="even">
<td><strong>Preserve byte order mark</strong></td>
<td>Specifies whether to add a byte order mark (BOM) to the documents produced by the assembler component.<br />
<br />
Default value: True</td>
</tr>
<tr class="odd">
<td><strong>Processing instruction scope</strong></td>
<td>Specifies whether the processing instruction is defined on the outermost envelope or at the document level.<br />
<br />
Default value: Document</td>
</tr>
<tr class="even">
<td><strong>Target charset</strong></td>
<td>Identify the character set used for the encoding of outgoing messages.<br />
<br />
Default value: (None)</td>
</tr>
</tbody>
</table>


## See Also

[Using Pipeline Designer](https://msdn.microsoft.com/en-us/library/aa578392\(v=bts.80\))  
[How to Configure the XML Assembler Pipeline Component](https://msdn.microsoft.com/en-us/library/aa560698\(v=bts.80\))  
[XML Information Set Elements in the XML Assembler Pipeline Component](https://msdn.microsoft.com/en-us/library/aa560313\(v=bts.80\))  
[Character Encoding in the XML Assembler Pipeline Component](https://msdn.microsoft.com/en-us/library/aa578435\(v=bts.80\))  
[Unrecognized Messages in the XML Assembler Pipeline Component](https://msdn.microsoft.com/en-us/library/aa561454\(v=bts.80\))  
[Document Structure Enforcement in the XML Assembler Pipeline Component](https://msdn.microsoft.com/en-us/library/aa578455\(v=bts.80\))  
[Processing Instructions in the XML Assembler Pipeline Component](https://msdn.microsoft.com/en-us/library/aa578687\(v=bts.80\))

