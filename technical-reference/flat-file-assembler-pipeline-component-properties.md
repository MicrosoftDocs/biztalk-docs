---
title: Flat File Assembler Pipeline Component Properties
TOCTitle: Flat File Assembler Pipeline Component Properties
ms:assetid: ea54099a-c907-4f51-b020-747534a4b907
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561722(v=BTS.80)
ms:contentKeyID: 51533169
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- Microsoft.BizTalk.Component.FFAsmComp
---

# Flat File Assembler Pipeline Component Properties

 

Use the Flat file assembler pipeline component to serialize XML documents into a flat file format and optionally add a header and/or trailer to it.

The Flat file assembler pipeline component is intended for use in the Assemble stage of the Send pipeline.

The properties of the Flat file assembler pipeline component can be set in the Properties window of Microsoft Visual Studio. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable Flat file assembler pipeline component properties.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Document schema</strong></td>
<td>Select a flat file document schema to use for serializing the message from XML to the flat file format. If no schema is specified, runtime schema discovery will be used.<br />
<br />
Default value: (None)</td>
</tr>
<tr class="even">
<td><strong>Header schema</strong></td>
<td>Select a schema for the header part of the flat file message. If no schema is specified, but header information is available at runtime, the corresponding header will be used.<br />
<br />
Default value: (None)</td>
</tr>
<tr class="odd">
<td><strong>Preserve byte order mark</strong></td>
<td>Specifies whether to add a byte order mark (BOM) to the documents produced by the assembler component.<br />
<br />
Default value: False</td>
</tr>
<tr class="even">
<td><strong>Target charset</strong></td>
<td>Identify the character set used for the encoding of outgoing messages.<br />
<br />
Default value: (None)</td>
</tr>
<tr class="odd">
<td><strong>Trailer schema</strong></td>
<td>Select a schema for the trailer part of a flat file message.<br />
<br />
Default value: (None)</td>
</tr>
</tbody>
</table>


## See Also

[Using Pipeline Designer](https://msdn.microsoft.com/library/aa578392\(v=bts.80\))  
[How to Configure the Flat File Assembler Pipeline Component](https://msdn.microsoft.com/library/aa560332\(v=bts.80\))  
[Character Encoding in the Flat File Assembler Pipeline Component](https://msdn.microsoft.com/library/aa547314\(v=bts.80\))  
[Property Demotion in Assembler Pipeline Components](https://msdn.microsoft.com/library/aa547894\(v=bts.80\))  
[Document Structure Enforcement in the Flat File Assembler Pipeline Component](https://msdn.microsoft.com/library/aa559659\(v=bts.80\))  
[How to Configure the Flat File Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa578441\(v=bts.80\))

