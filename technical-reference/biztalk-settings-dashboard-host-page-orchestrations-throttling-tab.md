---
description: "Learn more about: BizTalk Settings Dashboard, Host Page, Orchestrations Throttling Tab"
title: BizTalk Settings Dashboard, Host Page, Orchestrations Throttling Tab
TOCTitle: BizTalk Settings Dashboard, Host Page, Orchestrations Throttling Tab
ms:assetid: 9f0541d6-b20d-4b9d-983c-a230475922ce
ms:mtpsurl: https://msdn.microsoft.com/library/Ff629749(v=BTS.80)
ms:contentKeyID: 51530025
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: how-to
---

# BizTalk Settings Dashboard, Host Page, Orchestrations Throttling Tab

 

Use the **Orchestrations Throttling** tab to modify the orchestration throttling settings and limiting the number of outstanding messages it can have. This prevents an orchestration from consuming too much memory.

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
<td><strong>Host</strong></td>
<td>From the drop-down box, select the host representing the BizTalk Server runtime instances.</td>
<td>-</td>
<td>-</td>
</tr>
<tr class="even">
<td><strong>Dehydration behavior</strong></td>
<td>Select the dehydration behavior of the orchestration (XLANG) engine. Note that the other XLANG settings are editable only if you select “Custom”.<br />
<br />
 BizTalk Server uses the dehydration properties to decide when to dehydrate and rehydrate orchestrations. Under normal load, the default dehydration values are sufficient, but if you are running under heavy load and want to change the performance characteristics, you should tune the values. The dehydration behavior of BizTalk Server depends entirely on how much memory is available and how much memory is being used.</td>
<td>Always<br />
<br />
Never<br />
<br />
Custom</td>
<td>Custom</td>
</tr>
</tbody>
</table>


**Time Based**

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
<td><strong>Maximum threshold</strong></td>
<td>Specify the maximum idle time an orchestration instance could be blocked before being dehydrated.</td>
<td>(MinThreshold – Maximum value of type Integer]</td>
<td>1800 sec</td>
</tr>
<tr class="even">
<td><strong>Minimum threshold</strong></td>
<td>Specify the minimum idle time an orchestration instance could be blocked before being dehydrated.</td>
<td>[1 – Maximum value of type Integer</td>
<td>1sec</td>
</tr>
</tbody>
</table>


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
<td><strong>Subscriptions</strong></td>
<td>Select this option to manually set the ‘pause at’ and ‘resume at’ values for a subscription. By default, the system takes care of the subscriptions at runtime.</td>
<td>On, Off</td>
<td>Off</td>
</tr>
<tr class="even">
<td><strong>Pause at</strong></td>
<td>Specify the maximum number of messages you want a subscription to store.<br />
<br />
When a subscription has messages waiting to be consumed that are greater than or equal to the specified number, the messages are not delivered to the subscription instance. The minimum number of messages would be the ‘resume at’ value.<br />
<br />
For example, if you set <strong>Pause at</strong> value to 100, it means an orchestration has 100 outstanding messages and the MessageBox will stop sending additional messages.</td>
<td>(ResumeAt – Maximum value of type Integer]. Except when both are 0.</td>
<td>Off</td>
</tr>
<tr class="odd">
<td><strong>Resume at</strong></td>
<td>Specify the number of messages you want the MessageBox to resume sending messages to subscription.<br />
<br />
For example, set the <strong>Resume at</strong> value to 50. When the orchestration's number of outstanding messages is down to 50, it specifies that MessageBox can resume sending messages.</td>
<td>[0 – Maximum value of type Integer)</td>
<td>Off</td>
</tr>
</tbody>
</table>


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
<td><strong>Restore Defaults</strong></td>
<td>Click to cancel the modifications done and apply the default BizTalk Server settings.</td>
<td>-</td>
<td>-</td>
</tr>
</tbody>
</table>


## See Also

[How to Modify Group Settings](https://msdn.microsoft.com/library/ff629808\(v=bts.80\))  
[How to Modify Host Instance Settings](https://msdn.microsoft.com/library/ff629695\(v=bts.80\))

