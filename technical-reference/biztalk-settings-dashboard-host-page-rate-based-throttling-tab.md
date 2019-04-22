---
title: BizTalk Settings Dashboard, Host Page, Rate Based Throttling Tab
TOCTitle: BizTalk Settings Dashboard, Host Page, Rate Based Throttling Tab
ms:assetid: 1c75659d-246f-4666-a62e-5c7ee7d777e9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff629691(v=BTS.80)
ms:contentKeyID: 51526585
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# BizTalk Settings Dashboard, Host Page, Rate Based Throttling Tab

 

Use the **Rate Based Throttling** tab to modify the settings of host instance that contain orchestrations or send adapters that receive and deliver or process messages that have been published to the MessageBox.

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
</tbody>
</table>


**Publishing**

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
<td><strong>Minimum number of samples</strong></td>
<td>Specify the minimum number of messages BizTalk Server will sample for the <strong>Sampling window duration</strong> before considering rate-based throttling.<br />
<br />
If the actual number of samples in a sampling window fall below this value, then the samples are discarded and throttling is not applied. This value should be consistent with a rate at which messages can be published under a medium load. For example, if your system is expected to handle 1,000 documents per second under a medium load, then this parameter should be set to 1,000 * Sample window duration in seconds. If the value is set too low, then the system may experience a throttling condition under low load. If the value is set too high, then there may not be enough samples for this technique to be effective.</td>
<td>1 – Max value of type Integer</td>
<td>100</td>
</tr>
<tr class="even">
<td><strong>Sampling window duration</strong></td>
<td>Specify the time-window (measured in seconds), which is used to calculate the publishing rate based on the samples collected. The duration should be increased if the latency required for publishing a single message is high.</td>
<td>1 – Max value of type Integer</td>
<td>15 sec</td>
</tr>
<tr class="odd">
<td><strong>Rate overdrive factor</strong></td>
<td>Specify the percent to control how much higher you allow the request rate to be than the completion rate before a throttling condition occurs.<br />
<br />
For example, if messages are being published at a rate of 200 per second and this parameter is set to 125, then the system allows the publication of up to 250 messages per second (125% * 200 = 250) before applying throttling. Specifying too small a value for this parameter can cause the system to throttle more aggressively and could lead to over-throttling. Specifying too large a value for this parameter can cause under throttling and prevent the throttling mechanism from recognizing a legitimate throttling condition.</td>
<td>1 – Max value of type Integer</td>
<td>125</td>
</tr>
<tr class="even">
<td><strong>Maximum throttling delay</strong></td>
<td>Specify the maximum delay (in seconds) BizTalk Server imposes on a message instance due to throttling. The actual delay depends on the severity of the throttling condition.</td>
<td>1 – Max value of type Integer</td>
<td>300 sec</td>
</tr>
<tr class="odd">
<td><strong>Throttling override</strong></td>
<td>Specify if you want to override message publishing throttling.</td>
<td>0: Do not override<br />
<br />
1: Initiate throttling condition<br />
<br />
2: Do not throttle</td>
<td>0</td>
</tr>
<tr class="even">
<td><strong>Throttling override severity</strong></td>
<td>Specify the severity of an inbound throttling condition.<br />
<br />
A higher value increases the severity of an inbound throttling condition initiated when <strong>Throttling override</strong> is set to 1.</td>
<td>1 – 1000</td>
<td>100</td>
</tr>
</tbody>
</table>


**Delivery**

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
<td><strong>Minimum number of samples</strong></td>
<td>Specify the minimum number of messages BizTalk Server will sample for the <strong>Sampling window duration</strong> before considering rate-based throttling.<br />
<br />
If the actual number of samples in a sampling window falls below this value, then the samples are discarded and throttling is not applied. This value should be consistent with a rate at which messages can be delivered under a medium load. For example, if your system is expected to handle 1,000 documents per second under a medium load, then this parameter should be set to 1,000 * Sample window duration in seconds.<br />
<br />
If the value is set too low, then the system may experience a throttling condition under low load. If the value is set too high, then there may not be enough samples for this technique to be effective.</td>
<td>1 – Max value of type Integer</td>
<td>100</td>
</tr>
<tr class="even">
<td><strong>Sampling window duration</strong></td>
<td>Specify the time-window (in seconds), which is used to calculate the processing rate based on the samples collected. The duration should be increased if the latency required for processing a single message is high.</td>
<td>1 – Max value of type Integer</td>
<td>15 sec</td>
</tr>
<tr class="odd">
<td><strong>Rate overdrive factor</strong></td>
<td>Specify the percent to control how much higher you allow the delivery rate to the Orchestration or Messaging engine to be than the completion rate before a throttling condition occurs.<br />
<br />
For example, if messages are being processed at a rate of 200 per second and this parameter is set to 125, then the system allows the processing of up to 250 messages per second (125% * 200 = 250) before applying throttling. Specifying too small a value for this parameter causes the system to throttle more aggressively and could lead to over throttling. Specifying too large a value for this parameter causes under throttling and prevent the throttling mechanism from recognizing a legitimate throttling condition.</td>
<td>1 – Max value of type Integer</td>
<td>125</td>
</tr>
<tr class="even">
<td><strong>Maximum throttling delay</strong></td>
<td>Specify the maximum delay BizTalk Server imposes on a message instance due to throttling. The actual delay depends on the severity of the throttling condition.</td>
<td>1 – Max value of type Integer</td>
<td>300 sec</td>
</tr>
<tr class="odd">
<td><strong>Throttling override</strong></td>
<td>Specify if you want to override message delivery throttling.</td>
<td>0: Do not override<br />
<br />
1: Initiate throttling condition<br />
<br />
2: Do not throttle</td>
<td>0</td>
</tr>
<tr class="even">
<td><strong>Throttling override severity</strong></td>
<td>Specify the severity of the outbound throttling condition.<br />
<br />
A higher value increases the severity of an outbound throttling condition initiated when <strong>Throttling override</strong> is set to 1.</td>
<td>1 – 1000</td>
<td>100</td>
</tr>
<tr class="odd">
<td><strong>Restore Defaults</strong></td>
<td>Click to cancel the modifications and apply the default BizTalk Server settings.</td>
<td>-</td>
<td>-</td>
</tr>
</tbody>
</table>


## See Also

[How to Modify Group Settings](https://msdn.microsoft.com/library/ff629808\(v=bts.80\))  
[How to Modify Host Instance Settings](https://msdn.microsoft.com/library/ff629695\(v=bts.80\))

