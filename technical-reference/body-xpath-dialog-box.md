---
title: Body XPath Dialog Box
TOCTitle: Body XPath Dialog Box
ms:assetid: 13cfe362-46d7-47c0-ae4f-6d068ffd4859
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547627(v=BTS.80)
ms:contentKeyID: 51526391
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.editor.body.xpath
---

# Body XPath Dialog Box

 

Use the **Body XPath** dialog box to provide the XPath to the body of the message associated with enveloped instance messages governed by this schema. The specified XPath indicates the node that serves as the root of the contents (body) of the envelope. Although this content is generally the instance message itself, it can also be a nested envelope.

The **Body XPath** property can only be set using this dialog box when the **Envelope** property of the **Schema** node is set to **Yes**, indicating that this schema describes an envelope.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Expandable subset of the schema tree</strong></td>
<td>Expand as necessary to select the node that represents the root node of the document body. The displayed tree is the subset of the schema tree that begins with the root <strong>Record</strong> node for which the <strong>Body XPath</strong> property is being set, and includes all of its descendants.</td>
</tr>
<tr class="even">
<td><strong>Edit box</strong></td>
<td>Specify the XPath that will be set as the value of the <strong>Body XPath</strong> property if you click <strong>OK</strong>. You can specify this XPath by:<br />
<br />
- Selecting a node in the expandable subset of the schema tree (recommended).<br />
- Typing a custom XPath into the edit box <strong>Note:</strong> Use caution when manually entering an XPath; its syntax makes it prone to errors.</td>
</tr>
</tbody>
</table>


## See Also

[Envelope Schemas](https://msdn.microsoft.com/library/aa578090\(v=bts.80\))  
[Envelope (Node Property of All Schemas)](envelope-node-property-of-all-schemas.md)

