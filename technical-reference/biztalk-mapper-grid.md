---
description: "Learn more about: BizTalk Mapper Grid"
title: BizTalk Mapper Grid
TOCTitle: BizTalk Mapper Grid
ms:assetid: 3ac092c0-a58b-4b8b-ac06-b7d8e729a489
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559658(v=BTS.80)
ms:contentKeyID: 51527383
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.mapper.grid
ms.topic: ui-reference
---

# BizTalk Mapper Grid

 

Use the grid within BizTalk Mapper to define how records and fields in your source schema map to records and fields in your destination schema.

If you drag a record or field in the source or destination schema directly to a record or field in the other schema, the link connecting these fields will be routed through the BizTalk Mapper grid.

If a particular mapping requires the use of one or more functoids, first drag and drop the appropriate functoid(s) from the appropriate functoid category tab in the Microsoft Visual Studio toolbox to the BizTalk Mapper grid. Then create the links between the functoid(s) and the appropriate records or fields in the source and destination schema by dragging the functoid, record, or field to the functoid, record, or field with which you want it to be linked. Links can be created in either direction.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Large white arrows that appear when you put the cursor near an edge or corner of the grid.<br />
<br />
Examples:<br />
<br />
 <strong>Grid scrolling arrow - northeast</strong><br />
<br />
 <img src="images/Aa559658.f0b985cd-c66d-44b9-8c91-9292b1449284(BTS.80).jpeg" alt="Icon that represents the Grid scrolling arrow - northeast."/><br />
<br />
 <strong>Grid scrolling arrow - west</strong><br />
<br />
 <img src="images/Aa559658.9d582372-2061-4fa1-a6b6-992759d997f7(BTS.80).jpeg" alt="Icon that represents the Grid scrolling arrow - west."/></td>
<td>Scroll the grid in the direction of the arrow to show a portion of the grid that was not previously viewable.</td>
</tr>
<tr class="even">
<td>Functoid category tabs in the Visual Studio toolbox.</td>
<td>Expose sets of related functoids that you can drag to the grid.</td>
</tr>
<tr class="odd">
<td><strong>First grid page button</strong><br />
<br />
 <img src="images/Aa559658.dc05ce6f-d98d-41c8-82f3-38e128ebfaa3(BTS.80).jpeg" alt="Icon that represents the First grid page button."/></td>
<td>Scrolls the page tab to view the first grid page.</td>
</tr>
<tr class="even">
<td><strong>Previous grid page button</strong><br />
<br />
 <img src="images/Aa559658.0b36db3b-07bc-420b-94a5-d11a395cd5bf(BTS.80).jpeg" alt="Icon that represents the Previous grid page button."/></td>
<td>Scrolls the next grid page to the left of the currently visible grid page so you can view it.</td>
</tr>
<tr class="odd">
<td><strong>Next grid page button</strong><br />
<br />
 <img src="images/Aa559658.627081ac-dea2-433d-b8b2-e4beb0fadf65(BTS.80).jpeg" alt="Icon that represents the Next grid page button."/></td>
<td>Scrolls the next grid page to the right of the currently visible grid page so you can view it.</td>
</tr>
<tr class="even">
<td><strong>Last grid page button</strong><br />
<br />
 <img src="images/Aa559658.54a3fbed-3ac0-4d5a-9dc5-a22fb9660141(BTS.80).jpeg" alt="Icon that represents the Last grid page button."/></td>
<td>Scrolls the page tab to view the last grid page.</td>
</tr>
<tr class="odd">
<td>Page <strong>&lt;N&gt;</strong> tab(s)</td>
<td>Bring the corresponding grid page to the top, so you can view it.<br />
<br />
Grid pages can be renamed; their default names are &quot;Page 1,&quot; &quot;Page 2,&quot; and so on.</td>
</tr>
<tr class="even">
<td><strong>Grid Preview</strong> command on the shortcut menu associated with the grid area.</td>
<td>Open the <strong>Grid Preview</strong> dialog box so you can navigate more effectively when working with large grids (map grid pages).<br />
<br />
This command is also available on the <strong>BizTalk</strong> menu.</td>
</tr>
<tr class="odd">
<td><strong>Add Page</strong> command on the shortcut menu associated with the page tabs.</td>
<td>Add a new grid page. New grid pages have a default name of the form &quot;Page <strong>N</strong>&quot;, where &quot;<strong>N</strong>&quot; is a monotonically increasing number starting at &quot;2.&quot;<br />
<br />
This command is also available on the <strong>BizTalk</strong> menu.</td>
</tr>
<tr class="even">
<td><strong>Delete Page</strong> command on the shortcut menu associated with the page tabs.</td>
<td>Delete the currently selected grid page. You will be prompted to confirm the deletion of the page and any links and functoids it contains.<br />
<br />
This command is also available on the <strong>BizTalk</strong> menu.</td>
</tr>
<tr class="odd">
<td><strong>Rename Page</strong> command on the shortcut menu associated with the page tabs.</td>
<td>Rename the currently selected grid page.<br />
<br />
This command is also available on the <strong>BizTalk</strong> menu.</td>
</tr>
<tr class="even">
<td><strong>Reorder Pages</strong> command on the shortcut menu associated with the page tabs.</td>
<td>Open the <strong>Reorder Pages</strong> dialog box within which the order of grid pages can be rearranged.<br />
<br />
This command is also available on the <strong>BizTalk</strong> menu. <strong>Note:</strong> This command is not available unless there is more than one grid page.</td>
</tr>
</tbody>
</table>


## See Also

[Grid Properties](grid-properties.md)

