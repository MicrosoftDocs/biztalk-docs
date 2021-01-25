---
description: "Learn more about: New Dimension Dialog Box"
title: New Dimension Dialog Box
TOCTitle: New Dimension Dialog Box
ms:assetid: f8fc8a9d-b52a-400f-9ef8-1925340ca21f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562026(v=BTS.80)
ms:contentKeyID: 51533529
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts06.bam.workbook.newdimension
---

# New Dimension Dialog Box

 

Use the **New Dimension** dialog box to create a new category in an Analysis Services (OLAP) cube to describe the data contained in a table.

The contents of the New Dimension dialog box change based on the dimension type you choose. You can create the following types of dimensions:

  - **Data Dimension**. A dimension that you use to categorize the aggregations based on the value of some text items in the BAM activity.

  - **Numeric Range Dimension**. A dimension that enables you to categorize aggregations based on friendly names of given numeric ranges.

  - **Progress Dimension**. A dimension to represent the creation of aggregations with respect to the progress of activities that are still in process.

  - **Time Dimension**. A dimension that enables you to create aggregations for defined time segments.

The following table shows the details for the New Dimension dialog box when you create a data dimension.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Dimension name</strong></td>
<td>Type a descriptive name for the dimension you are creating.</td>
</tr>
<tr class="even">
<td><strong>Dimension type</strong></td>
<td>From the drop-down list, select Data Dimension.</td>
</tr>
<tr class="odd">
<td><strong>Available data items</strong></td>
<td>Select the item or items that you want to include in the dimension.</td>
</tr>
<tr class="even">
<td><strong>Dimension levels</strong></td>
<td>Select the item or items that you want to remove from the dimension or change the order of in the dimension.</td>
</tr>
<tr class="odd">
<td><strong>Add</strong></td>
<td>Click to add the items selected in the Available data items list.</td>
</tr>
<tr class="even">
<td><strong>Add All</strong></td>
<td>Click to add all of the items in the Available data items list.</td>
</tr>
<tr class="odd">
<td><strong>Remove</strong></td>
<td>Click to remove the selected item from the Dimension levels list.</td>
</tr>
<tr class="even">
<td><strong>Remove All</strong></td>
<td>Click to remove all of the data items from the Dimension levels list.</td>
</tr>
<tr class="odd">
<td><strong>Move Up</strong></td>
<td>Click to move the selected data item up in the Dimension levels list.</td>
</tr>
<tr class="even">
<td><strong>Move Down</strong></td>
<td>Click to move the selected data item down in the Dimension levelslist.</td>
</tr>
</tbody>
</table>


The following table shows the details for the New Dimension dialog box when you create a numeric range dimension.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Dimension name</strong></td>
<td>Type a descriptive name for the dimension you are creating.</td>
</tr>
<tr class="even">
<td><strong>Dimension type</strong></td>
<td>From the drop-down list, select Numeric Range Dimension. <strong>Note:</strong> You must create at least two ranges.</td>
</tr>
<tr class="odd">
<td><strong>Base data item</strong></td>
<td>From the drop-down list, select the base data item for the numeric range dimension.</td>
</tr>
<tr class="even">
<td><strong>Available ranges</strong></td>
<td>Select a range you want to edit or delete.</td>
</tr>
<tr class="odd">
<td><strong>New Range</strong></td>
<td>Click to create a new range for the dimension. The New Range dialog box opens.</td>
</tr>
<tr class="even">
<td><strong>Edit</strong></td>
<td>Click to edit the selected range.</td>
</tr>
<tr class="odd">
<td><strong>Delete</strong></td>
<td>Click to delete the selected range.</td>
</tr>
</tbody>
</table>


The following table shows the details for the New Dimension dialog box when you create a progress dimension.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Dimension name</strong></td>
<td>Type a descriptive name for the dimension you are creating.</td>
</tr>
<tr class="even">
<td><strong>Dimension type</strong></td>
<td>From the drop-down list, select Progress Dimension.</td>
</tr>
<tr class="odd">
<td><strong>Progress milestones and stages</strong></td>
<td>Select a stage for which you want to create a child or sibling, or which you want to edit or delete.</td>
</tr>
<tr class="even">
<td><strong>New Stage</strong></td>
<td>Click to create a new transient child stage. If you want to create the child stage in relation to an existing stage, in the Progress stages list, select the existing stage, and then click New Child. Opens the New Progress Stage dialog box. <strong>Important:</strong> Child stages must be created before sibling stages.</td>
</tr>
<tr class="odd">
<td><strong>New Milestone</strong></td>
<td>Click to create a new non-transient sibling stage. If you want to create the sibling stage in relation to an existing stage, in the Progress stages list, select the existing stage, and then click New Sibling. Opens the New Progress Stage dialog box.</td>
</tr>
<tr class="even">
<td><strong>Edit</strong></td>
<td>Click to edit the selected progress stage.</td>
</tr>
<tr class="odd">
<td><strong>Delete</strong></td>
<td>Delete the selected progress stage.</td>
</tr>
</tbody>
</table>


The following table shows the details for the New Dimension dialog box when you create a time dimension.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Dimension name</strong></td>
<td>Type a descriptive name for the dimension you are creating.</td>
</tr>
<tr class="even">
<td><strong>Dimension type</strong></td>
<td>From the drop-down list, select Time Dimension.</td>
</tr>
<tr class="odd">
<td><strong>Base business milestone</strong></td>
<td>From the drop-down list, select the base business milestone for the time dimension.</td>
</tr>
<tr class="even">
<td><strong>Year, quarter, month</strong></td>
<td>Click to display aggregate data by year, quarter, and month.</td>
</tr>
<tr class="odd">
<td><strong>Year, quarter, month, day</strong></td>
<td>Click to display aggregate data by year, quarter, month, and day.</td>
</tr>
<tr class="even">
<td><strong>Year, quarter, month, day, hour, minute</strong></td>
<td>Click to display aggregate data by year, quarter, month, day, hour, and minutes.</td>
</tr>
<tr class="odd">
<td><strong>Year, month</strong></td>
<td>Click to display aggregate data by year and month.</td>
</tr>
<tr class="even">
<td><strong>Year, month, day</strong></td>
<td>Click to display aggregate data by year, month, and day.</td>
</tr>
<tr class="odd">
<td><strong>Year, month, day, hour minute</strong></td>
<td>Click to display aggregate data by year, month, day, hour, and minutes.</td>
</tr>
<tr class="even">
<td><strong>Year, week</strong></td>
<td>Click to display aggregate data by year and week.</td>
</tr>
<tr class="odd">
<td><strong>Year, week, day</strong></td>
<td>Click to aggregate data by year, week, and day.</td>
</tr>
<tr class="even">
<td><strong>Year, week, day, hour, minute</strong></td>
<td>Click to display aggregate data by year, week, day, hour, and minutes.</td>
</tr>
</tbody>
</table>


## See Also

[Defining Dimensions](https://msdn.microsoft.com/library/aa578432\(v=bts.80\))

