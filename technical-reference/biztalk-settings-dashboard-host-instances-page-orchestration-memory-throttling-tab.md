---
title: BizTalk Settings Dashboard, Host Instances Page, Orchestration Memory Throttling Tab
TOCTitle: BizTalk Settings Dashboard, Host Instances Page, Orchestration Memory Throttling Tab
ms:assetid: d1686113-09b0-402b-876d-b8fd058bcdb0
ms:mtpsurl: https://msdn.microsoft.com/library/Ff629779(v=BTS.80)
ms:contentKeyID: 51531515
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# BizTalk Settings Dashboard, Host Instances Page, Orchestration Memory Throttling Tab

 

Use the **Orchestration Memory Throttling** tab to continuously monitor for a throttling condition, calculate the severity of the throttling condition, and apply host instance memory throttling progressively depending on the calculated severity.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
<th>Boundary values</th>
<th>Default value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Host Instance</strong></td>
<td>From the drop-down box, select the running instance of a host on the BizTalk Server runtime machine.</td>
<td>-</td>
<td>-</td>
</tr>
</tbody>
</table>


**Physical**

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
<th>Boundary values</th>
<th>Default value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Optimal usage</strong></td>
<td>Specify the percentage of physical memory usage at which dehydration throttling comes into effect. This is the optimum percentage of physical memory to use for the host instances.</td>
<td>[0 – 100]</td>
<td>70</td>
</tr>
<tr class="even">
<td><strong>Maximal usage</strong></td>
<td>Specify the percentage of physical memory usage at which dehydration throttling is maximum. This is the maximum percentage of physical memory to use for the host instances.<br />
<br />
The minimum value of maximal usage should be <strong>Optimal usage</strong>.</td>
<td>(Optimal usage – 100]<br />
<br />
Except when both are 0 or 100.</td>
<td>85</td>
</tr>
</tbody>
</table>


**Virtual**

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
<th>Boundary values</th>
<th>Default value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Optimal usage</strong></td>
<td>Specify the percentage of virtual memory usage at which dehydration throttling comes into effect.<br />
<br />
At this point, <strong>TestThreshold</strong> has the value <strong>MaxThreshold</strong> and any memory usage greater than <strong>OptimalUsage</strong> causes <strong>TestThreshold</strong> to be less than <strong>MaxThreshold</strong>.</td>
<td>[0 – 100]</td>
<td>65</td>
</tr>
<tr class="even">
<td><strong>Maximal usage</strong></td>
<td>Specify the percentage of virtual memory usage at which dehydration throttling is maximum.<br />
<br />
At this point, <strong>TestThreshold</strong> has the value <strong>MinThreshold</strong> and any memory usage less than <strong>MaximalUsage</strong> causes <strong>TestThreshold</strong> to be greater than <strong>MinThreshold</strong>.</td>
<td>(Optimal usage – 100]<br />
<br />
Except when both are 0 or 100.</td>
<td>85</td>
</tr>
<tr class="odd">
<td><strong>Restore Defaults</strong></td>
<td>Click to cancel the modifications done and apply the default BizTalk Server settings.</td>
<td>-</td>
<td>-</td>
</tr>
</tbody>
</table>


## See Also

[How to Modify Group Settings](https://msdn.microsoft.com/library/ff629808\(v=bts.80\))  
[How to Modify Host Settings](https://msdn.microsoft.com/library/ff629679\(v=bts.80\))

