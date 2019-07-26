---
title: Generate Schemas Dialog Box
TOCTitle: Generate Schemas Dialog Box
ms:assetid: 82747abd-2e73-40e3-9b49-9d8d09505ca1
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561107(v=BTS.80)
ms:contentKeyID: 51529322
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.editor.schemas.generate
---

# Generate Schemas Dialog Box

 

Use the **Generate Schemas** dialog box to generate an XSD-based BizTalk Server schema from one of the following input sources:

  - A valid XML-data reduced (XDR) schema.

  - A valid document type definition (DTD).

  - A well-formed XML instance message that the XSD schema will describe.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Document type</strong></td>
<td>Select the type of input file from which the schema will be generated. The drop-down list contains three entries, one for each of the supported input sources.</td>
</tr>
<tr class="even">
<td><strong>Input file / Browse</strong></td>
<td>Type, paste, or browse for the name of the input file that matches your selection for the type of the input file.</td>
</tr>
</tbody>
</table>


The schema generation modules for DTDs and well-formed XML are not loaded by default, as indicated by the string "(Not loaded)" appended to the relevant drop-down list selections. You must run the scripts InstallDTD.vbs and/or InstallWFX.vbs to load the DTD and well-formed XML schema generation modules, respectively. These scripts are in the following folder:

\<*InstallationPath*\>\\SDK\\Utilities\\Schema Generator

## See Also

[How to Migrate XDR Schemas to XSD Schemas](https://msdn.microsoft.com/library/aa561382\(v=bts.80\))

