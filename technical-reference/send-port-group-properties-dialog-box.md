---
title: Send Port Group Properties Dialog Box
TOCTitle: Send Port Group Properties Dialog Box
ms:assetid: 6876e80c-f760-4bbc-be21-0d29cb6b9db3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560579(v=BTS.80)
ms:contentKeyID: 51528650
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.sendportgroup.properties
---

# Send Port Group Properties Dialog Box

 

You can bind Send Port Groups (SPG) to orchestration ports or use them for Content-based Routing (CBR) just as you can for a single send port.

## General Tab

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Name</strong></td>
<td>Type a name for the send port group.</td>
</tr>
<tr class="even">
<td><strong>Remove</strong></td>
<td>Click to remove the selected send port from the group.</td>
</tr>
<tr class="odd">
<td><strong>Properties</strong></td>
<td>Click to display properties for the selected send port.</td>
</tr>
<tr class="even">
<td><strong>Send ports - Name</strong></td>
<td>Select the name of a send port to add to the send port group.</td>
</tr>
<tr class="odd">
<td><strong>Send ports - URI</strong></td>
<td>Displays the address of a send port that has been added to the group.</td>
</tr>
<tr class="even">
<td><strong>Description</strong></td>
<td>Type any text that helps you distinguish this send port group from others. The maximum number of characters allowed is 256.</td>
</tr>
</tbody>
</table>


## Filters Tab

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Delete</strong></td>
<td>Click to delete the selected filter expression.</td>
</tr>
<tr class="even">
<td><strong>Move Up</strong></td>
<td>Click to move the selected property ahead in the filter expression sequence.</td>
</tr>
<tr class="odd">
<td><strong>Move Down</strong></td>
<td>Click to move the selected property down in the filter expression sequence.</td>
</tr>
<tr class="even">
<td><strong>Property</strong></td>
<td>Select a property reference to be used on messages transiting the port.</td>
</tr>
<tr class="odd">
<td><strong>Operator</strong></td>
<td>Type or select the operator for the expression.</td>
</tr>
<tr class="even">
<td><strong>Value</strong></td>
<td>Type the value to validate against the property.</td>
</tr>
<tr class="odd">
<td><strong>Group by</strong></td>
<td>Select <strong>And</strong> or <strong>Or</strong> to indicate the relationship between two filter expressions.</td>
</tr>
</tbody>
</table>


## See Also

[How to Enlist a Send Port or Send Port Group](https://msdn.microsoft.com/library/aa578592\(v=bts.80\))  
[Managing Send Ports and Send Port Groups](https://msdn.microsoft.com/library/aa561407\(v=bts.80\))  
[How to Start a Send Port or Send Port Group](https://msdn.microsoft.com/library/aa561872\(v=bts.80\))  
[How to Stop a Send Port or Send Port Group](https://msdn.microsoft.com/library/aa577932\(v=bts.80\))  
[How to Unenlist a Send Port or Send Port Group](https://msdn.microsoft.com/library/aa559480\(v=bts.80\))  
[Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\))

