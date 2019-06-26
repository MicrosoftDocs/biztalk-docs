---
title: Flat File Disassembler Pipeline Component Properties
TOCTitle: Flat File Disassembler Pipeline Component Properties
ms:assetid: 579f9da1-fbdc-4733-846d-cdb6495b8d74
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560266(v=BTS.80)
ms:contentKeyID: 51528188
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- Microsoft.BizTalk.Component.FFDasmComp
---

# Flat File Disassembler Pipeline Component Properties

 

Use the Flat file disassembler pipeline component to parse raw data into one or more documents and optionally remove headers and/or trailers.

The Flat file disassembler pipeline component is intended for use in the Disassemble stage of a Receive pipeline.

The properties of the Flat file disassembler pipeline component can be set in the Properties window of Microsoft Visual Studio. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable Flat file disassembler pipeline component properties.

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
<td>Select a flat file document schema to use for parsing the message from flat file to XML format.<br />
<br />
Default Value: (None)</td>
</tr>
<tr class="even">
<td><strong>Header schema</strong></td>
<td>Select a schema for the header part of a flat file message.<br />
<br />
Default Value: (None)</td>
</tr>
<tr class="odd">
<td><strong>Preserve header</strong></td>
<td>Set this property to True if you need to store the flat file message header on the message context. Preserving the header of the flat file message enables the header structure and content to flow along with the message through the BizTalk Server and then use this when serializing the message back to a flat file format in the flat file assembler.<br />
<br />
When the preserved header is being serialized by the flat file assembler, the header document design-time property can lack the name of the header schema because this information can be obtained dynamically at run time.<br />
<br />
Default Value: False</td>
</tr>
<tr class="even">
<td><strong>Trailer schema</strong></td>
<td>Select a schema for the trailer part of the flat file message.<br />
<br />
Default Value: (None)</td>
</tr>
<tr class="odd">
<td><strong>Validate document structure</strong></td>
<td>Set this property to True if you need to validate all the parts of the flat file message (header, body, and trailer) to make sure they conform to their schemas. This option reduces the performance of the flat file disassembler so it is set to false by default.<br />
<br />
Default Value: False <strong>Note:</strong> You must specify a document schema (using the Document schema property) and have it deployed if you want to validate the document structure. If you fail to specify a document schema, you will receive a runtime error.</td>
</tr>
<tr class="even">
<td><strong>Recoverable interchange processing</strong></td>
<td>Indicate whether to process messages within an interchange individually. For more information, see <a href="https://msdn.microsoft.com/library/aa578714(v=bts.80)">Recoverable Interchange Processing</a><br />
<br />
Default Value: False</td>
</tr>
</tbody>
</table>


## See Also

[Using Pipeline Designer](https://msdn.microsoft.com/library/aa578392\(v=bts.80\))  
[How to Configure the Flat File Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa578441\(v=bts.80\))  
[Flat File Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa561315\(v=bts.80\))  
[Document Validation in the Flat File Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa561301\(v=bts.80\))  
[Character Encoding in the Flat File Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa547361\(v=bts.80\))  
[Extending the Flat File Disassembler Pipeline Component](https://msdn.microsoft.com/library/aa560024\(v=bts.80\))  
[Distinguished Fields in Disassembler Pipeline Components](https://msdn.microsoft.com/library/aa561024\(v=bts.80\))

