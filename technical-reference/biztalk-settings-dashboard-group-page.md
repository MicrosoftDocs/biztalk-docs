---
title: BizTalk Settings Dashboard, Group Page
TOCTitle: BizTalk Settings Dashboard, Group Page
ms:assetid: 16e0ac35-49da-448c-b6d7-06e714d9e957
ms:mtpsurl: https://msdn.microsoft.com/library/Ff629685(v=BTS.80)
ms:contentKeyID: 51526432
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# BizTalk Settings Dashboard, Group Page

 

Use the **Group** tab to modify the configuration of group-level performance settings in BizTalk Server.


> [!NOTE]
> <P>These settings are applicable for all the machines in a given group.</P>



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
<td><strong>Configuration refresh interval</strong></td>
<td>Set the interval in which BizTalk Server refreshes messaging configuration.</td>
<td>1 - 43200</td>
<td>-</td>
</tr>
<tr class="even">
<td><strong>Message Batch Threshold</strong></td>
<td>If the total size of an incoming message Batch exceeds this value, then it is split into smaller batches and processed.</td>
<td>1 - 10000000</td>
<td>102400</td>
</tr>
<tr class="odd">
<td><strong>Large message size</strong></td>
<td>Set the threshold size of an individual message that triggers streaming in a batch and/or during transformations.</td>
<td>1 - 10000000</td>
<td>1000000</td>
</tr>
</tbody>
</table>


**Tracking and Reporting**

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
<td><strong>Message box performance counter sampling interval</strong></td>
<td>Set the interval at which performance counters are refreshed.<br />
<br />
The interval trades off load on database versus up-to-dateness of counters. The higher value means less frequently updated data, and thus lesser load on the database.</td>
<td>1 – 1 – Maximum value of type Integer</td>
<td>-</td>
</tr>
<tr class="even">
<td><strong>Enable group level tracking</strong></td>
<td>Select this option to turn the group level tracking for BizTalk Server on.<br />
<br />
Turning off global tracking disables the tracking interceptors for the entire BizTalk Server group. This means, BizTalk Server will not track events in its tracking tables. <strong>Note:</strong> This setting does not impact BAM Tracking.</td>
<td>On, Off</td>
<td>On</td>
</tr>
<tr class="odd">
<td><strong>Allow import of tracking settings</strong></td>
<td>New starting with BizTalk Server 2016.<br />
<br />
When you import an application, the tracking settings configured on artifacts within the application are also imported. This is how all previous BizTalk versions behave. When unchecked, the tracking settings are not imported. This is a global setting, so it applies to all applications you import, and will import in the future.<br />
<br />
If you want to control what is specifically tracked in your environments, just as you have in previous BizTalk versions, then leave this setting enabled. If you want to disable tracking on all artifacts on all imported applications, then uncheck this setting.<br />
<br />
BTS task example:<br />
<code>btstask importbindings -ImportTrackingSettings:false -Source:c:\temp\binding.xml</code></td>
<td>On, Off</td>
<td>On</td>
</tr>
</tbody>
</table>


**Restore, import, and export**

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Restore Defaults</strong></td>
<td>Click to cancel the modifications done, and apply the default BizTalk Server settings.</td>
</tr>
<tr class="even">
<td><strong>Import</strong></td>
<td>Import the group, host, and host instance settings that have been exported from another group.</td>
</tr>
<tr class="odd">
<td><strong>Export</strong></td>
<td>Export the group, host, and host instances settings from this current BizTalk group, to an XML file.</td>
</tr>
</tbody>
</table>


## See Also

[How to Modify Host Settings](https://msdn.microsoft.com/library/ff629679\(v=bts.80\))  
[How to Modify Host Instance Settings](https://msdn.microsoft.com/library/ff629695\(v=bts.80\))

