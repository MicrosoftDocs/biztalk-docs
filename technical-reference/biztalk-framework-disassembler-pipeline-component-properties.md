---
title: BizTalk Framework Disassembler Pipeline Component Properties
TOCTitle: BizTalk Framework Disassembler Pipeline Component Properties
ms:assetid: c88cca43-21aa-41c1-87de-9b030510920c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547967(v=BTS.80)
ms:contentKeyID: 51531136
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- Microsoft.BizTalk.Component.BtfDasmComp
---

# BizTalk Framework Disassembler Pipeline Component Properties

 

Use the BizTalk Framework disassembler pipeline component to save the message context, and create a new message context with the BizTalk Framework property that needs to be generated.

The BizTalk Framework disassembler pipeline component is intended for use in the Disassemble stage of a Receive pipeline.

The properties of the BizTalk Framework disassembler pipeline component can be set in the Properties window of Microsoft Visual Studio. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable BizTalk Framework disassembler pipeline component properties.

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
<td>Indicate whether to allow messages that do not have a recognized schema to be passed through the disassembler.<br />
<br />
Default value: False</td>
</tr>
<tr class="even">
<td><strong>Document schemas</strong></td>
<td>Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see <a href="https://msdn.microsoft.com/en-us/library/aa559127(v=bts.80)">How to Use the Schema Collection Property Editor</a>.<br />
<br />
Default value: Empty collection (Collection)</td>
</tr>
<tr class="odd">
<td><strong>Envelope schemas</strong></td>
<td>Indicate the namespace and typename of the schema or schemas to be applied to the envelope. For more information, see <a href="https://msdn.microsoft.com/en-us/library/aa559127(v=bts.80)">How to Use the Schema Collection Property Editor</a>.<br />
<br />
Default value: (Collection), BTF2Schemas.btf2_envelope</td>
</tr>
<tr class="even">
<td><strong>Validate document structure</strong></td>
<td>Perform a validation of the incoming message to the disassembler, including validating the envelope(s), when set to True.<br />
<br />
Default value: False</td>
</tr>
</tbody>
</table>


## See Also

[Using Pipeline Designer](https://msdn.microsoft.com/library/aa578392\(v=bts.80\))  
[Envelope Use in the XML Assembler and Disassembler Pipeline Components](https://msdn.microsoft.com/library/aa548053\(v=bts.80\))  
[BizTalk Framework Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa559940\(v=bts.80\))  
[BizTalk Framework Schema and Properties](https://msdn.microsoft.com/library/aa561250\(v=bts.80\))  
[Configuring Native Pipeline Components](https://msdn.microsoft.com/library/aa577837\(v=bts.80\))

