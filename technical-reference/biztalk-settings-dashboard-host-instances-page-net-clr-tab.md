---
title: BizTalk Settings Dashboard, Host Instances Page, .NET CLR Tab
TOCTitle: BizTalk Settings Dashboard, Host Instances Page, .NET CLR Tab
ms:assetid: 050dc059-31e2-4eb2-9367-4af55da81a58
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff629678(v=BTS.80)
ms:contentKeyID: 51525980
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# BizTalk Settings Dashboard, Host Instances Page, .NET CLR Tab

 

When you need to update the number of Windows threads available in the .NET thread pool associated with an instance of a BizTalk host, use the **.NET CLR** tab to modify the appropriate CLR Hosting values in the registry of the BizTalk Server.

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
<tr class="even">
<td><strong>Threading Settings</strong></td>
<td></td>
<td>-</td>
<td>-</td>
</tr>
<tr class="odd">
<td><strong>Max. worker threads</strong></td>
<td>Specify the maximum number of .NET CLR worker threads.</td>
<td>[Min worker threads, 500]</td>
<td>25</td>
</tr>
<tr class="even">
<td><strong>Min. worker threads</strong></td>
<td>Specify the minimum number of .NET CLR worker threads.</td>
<td>[0, 500]</td>
<td>5</td>
</tr>
<tr class="odd">
<td><strong>Max. IO threads</strong></td>
<td>Specify the maximum number of IO threads.</td>
<td>[Min IO threads, 1000]</td>
<td>250</td>
</tr>
<tr class="even">
<td><strong>Min. IO threads</strong></td>
<td>Specify the minimum number of IO threads.</td>
<td>[0, 1000]</td>
<td>25</td>
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

[How to Modify Group Settings](https://msdn.microsoft.com/en-us/library/ff629808\(v=bts.80\))  
[How to Modify Host Settings](https://msdn.microsoft.com/en-us/library/ff629679\(v=bts.80\))

