---
title: BizTalk Framework Assembler Pipeline Component Properties
TOCTitle: BizTalk Framework Assembler Pipeline Component Properties
ms:assetid: 00179f6d-75ba-4cac-9136-dd1c1b2c05bf
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa546729(v=BTS.80)
ms:contentKeyID: 51525834
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- Microsoft.BizTalk.Component.BTFAsmComp
---

# BizTalk Framework Assembler Pipeline Component Properties

 

Use the BizTalk Framework assembler pipeline component to serialize the BizTalk Framework envelope and contents onto the message before transmission, resend in the event that a receipt does not arrive in the allotted time period, and receive and process the receipts when they come to delete the message instance.

The BizTalk Framework assembler pipeline component is intended for use in the Assemble stage of the Send pipeline.

The properties for the BizTalk Framework assembler pipeline component can be set in the Properties window of Microsoft Visual Studio. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable BizTalk Framework assembler pipeline component properties.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Add processing instructions text</strong></td>
<td>Allow the assembled XML documents to contain processing instructions as a value of this property. This also allows documents to contain instructions for applications. <strong>Note:</strong> Processing instruction text should conform to the W3C XML processing instruction standards.<br />
<br />
Default value: None</td>
</tr>
<tr class="even">
<td><strong>Add XML declaration</strong></td>
<td>Add an XML declaration to an outgoing message. When True, the following XML declaration is added to the outgoing message <code>&lt;?xml version='1.0' encoding='UTF8'&gt;</code>. The encoding specified depends on the encoding used by the BizTalk Framework assembler, which honors the specific runtime properties carrying the encoding information.<br />
<br />
Default value: True</td>
</tr>
<tr class="odd">
<td><strong>Delivery receipt address</strong></td>
<td>Indicate the address to which the delivery receipt for the BizTalk Framework document should be sent.<br />
<br />
Default value: None</td>
</tr>
<tr class="even">
<td><strong>Delivery receipt address type</strong></td>
<td>Indicate the type of address to which the delivery receipt for the BizTalk Framework document should be sent.<br />
<br />
Default value: biz: <strong>Note:</strong> The biz: prefix was used to signify organization identifiers for the source and destination endpoints in BizTalk 2000 and 2002, and for interoperability with those systems, the prefix is provided as a default here. For example, type = &quot;biz:OrganizationName&quot;, (src|dest) = &quot;Party1&quot;.</td>
</tr>
<tr class="odd">
<td><strong>Delivery receipt send by time</strong></td>
<td>Indicate the time (in minutes) by which the delivery receipt for the BizTalk Framework document must be received.<br />
<br />
Default value: 30</td>
</tr>
<tr class="even">
<td><strong>Destination address</strong></td>
<td>Identify the destination address.<br />
<br />
Default value: None</td>
</tr>
<tr class="odd">
<td><strong>Destination address type</strong></td>
<td>Indicate the destination address type.<br />
<br />
Default value: biz: <strong>Note:</strong> The biz: prefix was used to signify organization identifiers for the source and destination endpoints in BizTalk 2000 and 2002, and for interoperability with those systems, the prefix is provided as a default here. For example, type = &quot;biz:OrganizationName&quot;, (src|dest) = &quot;Party1&quot;.</td>
</tr>
<tr class="even">
<td><strong>Document schemas</strong></td>
<td>Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see <a href="https://msdn.microsoft.com/en-us/library/aa559127(v=bts.80)">How to Use the Schema Collection Property Editor</a>.<br />
<br />
Default value: (Collection) Empty collection</td>
</tr>
<tr class="odd">
<td><strong>Document topic</strong></td>
<td>Identify a URI reference that uniquely identifies the overall purpose of the BizTalk Framework document.<br />
<br />
Default value: None</td>
</tr>
<tr class="even">
<td><strong>Envelope schemas</strong></td>
<td>Indicate the namespace and typename of the schema or schemas that will be applied to the envelope. For more information, see <a href="https://msdn.microsoft.com/en-us/library/aa559127(v=bts.80)">How to Use the Schema Collection Property Editor</a>.<br />
<br />
Default value: (Collection), BTF2Schemas.btf2_envelope</td>
</tr>
<tr class="odd">
<td><strong>Generate delivery receipt request</strong></td>
<td>Indicate whether the delivery receipt request for the BizTalk Framework document should be generated. This is used to enable reliable messaging for the BizTalk Framework.<br />
<br />
Default value: False</td>
</tr>
<tr class="even">
<td><strong>Message time to live (in minutes)</strong></td>
<td>Specify the amount of time (in minutes) that the message will be valid.<br />
<br />
Default value: 30</td>
</tr>
<tr class="odd">
<td><strong>Add Processing instructions</strong></td>
<td>Specify how XML processing instructions are handled in the XML instance document.<br />
<br />
Append: The value of <strong>Add Processing Instructions Text</strong> should append to pre-existing processing instructions in the message.<br />
<br />
Create New: Thevalue of <strong>Add Processing Instructions Text</strong> entered in the field should overwrite or replace any pre-existing processing instructions in the message.<br />
<br />
If <strong>Create New</strong> is selected, then <strong>Add Processing Instructions Text</strong> must contain valid processing instructions.<br />
<br />
Ignore: If processing instructions text exists in the message, it is removed.<br />
<br />
Default Value: Append</td>
</tr>
<tr class="even">
<td><strong>Source address</strong></td>
<td>Identify the source address.<br />
<br />
Default value: None</td>
</tr>
<tr class="odd">
<td><strong>Source address type</strong></td>
<td>Indicate the source address type.<br />
<br />
Default value: biz: <strong>Note:</strong> The biz: prefix was used to signify organization identifiers for the source and destination endpoints in BizTalk 2000 and 2002, and for interoperability with those systems, the prefix is provided as a default here. For example, type = &quot;biz:OrganizationName&quot;, (src|dest) = &quot;Party1&quot;.</td>
</tr>
<tr class="even">
<td><strong>Target charset</strong></td>
<td>Identify the character set used for encoding of outgoing messages.<br />
<br />
Default value: (None)</td>
</tr>
</tbody>
</table>


## See Also

[Using Pipeline Designer](https://msdn.microsoft.com/library/aa578392\(v=bts.80\))  
[How to Create a New Pipeline](https://msdn.microsoft.com/library/aa578387\(v=bts.80\))  
[How to Open a Pipeline](https://msdn.microsoft.com/library/aa561730\(v=bts.80\))  
[How to Add a Component to a Pipeline](https://msdn.microsoft.com/library/aa560652\(v=bts.80\))  
[How to Set Pipeline Component Properties](https://msdn.microsoft.com/library/aa559409\(v=bts.80\))  
[How to Use the Schema Collection Property Editor](https://msdn.microsoft.com/library/aa559127\(v=bts.80\))  
[How to Save a Pipeline](https://msdn.microsoft.com/library/aa561936\(v=bts.80\))  
[How to Use the Toolbox](https://msdn.microsoft.com/library/aa560943\(v=bts.80\))  
[How to Navigate with the Keyboard](https://msdn.microsoft.com/library/aa559415\(v=bts.80\))  
[How to Read Pipeline Component Properties](https://msdn.microsoft.com/library/aa547568\(v=bts.80\))

