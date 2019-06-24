---
title: Transform Configuration Dialog Box
TOCTitle: Transform Configuration Dialog Box
ms:assetid: 7956489d-94ac-4e7d-b3a2-4a2fc059fd3c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560924(v=BTS.80)
ms:contentKeyID: 51529077
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.transform.config
---

# Transform Configuration Dialog Box

 

You use the **Transform Configuration** dialog box to configure the Transform shape. You assign a map to the Transform shape, either by creating a new one or by selecting an existing one, and you define source and destination messages to use in the transform.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>New Map</strong></td>
<td>Create a new map to do the transformation.</td>
</tr>
<tr class="even">
<td><strong>Existing Map</strong></td>
<td>Use an existing map to do the transformation.</td>
</tr>
<tr class="odd">
<td><strong>Fully Qualified Map Name</strong></td>
<td>Type a name for a new map, or use the drop-down list to select an existing map.</td>
</tr>
<tr class="even">
<td><strong>Source</strong></td>
<td>From the grid, select a source message for the transform. <strong>Note:</strong> Valid messages may be marked as invalid (red cross); this most often occurs when the message schema and map are in different projects. If your message is valid, you can safely ignore the invalid message icon.</td>
</tr>
<tr class="odd">
<td><strong>Destination</strong></td>
<td>From the grid, select a destination message for the transform. <strong>Note:</strong> Valid messages may be marked as invalid (red cross); this most often occurs when the message schema and map are in different projects. If your message is valid, you can safely ignore the invalid message icon.</td>
</tr>
<tr class="even">
<td><strong>When I click OK, launch the BizTalk Mapper</strong></td>
<td>Invoke the mapper to create or edit a map to use in the transform.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Transform Shape](https://msdn.microsoft.com/library/aa547996\(v=bts.80\))

