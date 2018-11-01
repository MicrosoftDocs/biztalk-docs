---
title: BizTalk Settings Dashboard, Host Page, Resource Based Throttling Tab
TOCTitle: BizTalk Settings Dashboard, Host Page, Resource Based Throttling Tab
ms:assetid: c37d700d-5fe6-4f31-97ae-92e0bcbc3589
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff629765(v=BTS.80)
ms:contentKeyID: 51531008
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# BizTalk Settings Dashboard, Host Page, Resource Based Throttling Tab

 

Use the **Resource Based Throttling** tab to manage the usage of system resources (such as threads, memory, and database size) by a host instance process.

<table>
<thead>
<tr class="header">
<th><strong>Use this</strong></th>
<th>To do this</th>
<th>Boundary values</th>
<th>Default value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Host</strong></td>
<td>From the drop-down list, select the host representing the BizTalk Server runtime instances.</td>
<td>-</td>
<td>-</td>
</tr>
<tr class="even">
<td><strong>Per CPU Settings</strong></td>
<td></td>
<td>-</td>
<td>-</td>
</tr>
<tr class="odd">
<td><strong>Threads</strong></td>
<td>Specify the maximum number of threads in the process (per CPU) allowed before the throttling begins.</td>
<td>[0, Maximum value of type Integer)</td>
<td>0</td>
</tr>
<tr class="even">
<td><strong>Database connections</strong></td>
<td>Specify the maximum number of database sessions (per CPU) allowed before throttling begins.</td>
<td>1 – Maximum value of type Integer</td>
<td>0</td>
</tr>
<tr class="odd">
<td><strong>In-process messages</strong></td>
<td>Specify the maximum number of messages delivered to the End Point Manager (EPM) or XLANG that have not been processed. This does not include the messages retrieved from database but still waiting for delivery in the in-memory queue.</td>
<td>1 – Maximum value of type Integer</td>
<td>1000</td>
</tr>
<tr class="even">
<td><strong>Internal message queue size</strong></td>
<td>Indicate the size of the in-memory queue. This queue serves as a temporary placeholder for delivering messages.<br />
<br />
Setting a large value for this parameter may improve low-latency scenarios to some extent since more messages will be proactively retrieved from the MessageBox database for processing. Since the messages in this queue consume memory, setting this parameter to a smaller value may be desirable for scenarios involving large messages in order to avoid memory based throttling of the process. <strong>Note:</strong> If you modify this value, the host needs to be restarted for the change to take effect.</td>
<td>1 – Maximum value of type Integer</td>
<td>100</td>
</tr>
<tr class="odd">
<td><strong>Message count in DB</strong></td>
<td>Indicate the total number of messages published by the host instance to the work, state, and suspended queues of the subscribing hosts.<br />
<br />
The <strong>Message count in DB</strong> setting also indirectly defines the threshold for a throttling condition based on the number of messages in the spool table or tracking table. If the number of messages in the spool table or tracking table exceeds 10 times this value then a throttling condition will be triggered.</td>
<td>1 – Maximum value of type Integer</td>
<td>50000</td>
</tr>
<tr class="even">
<td><strong>Memory Usage</strong></td>
<td></td>
<td>-</td>
<td>-</td>
</tr>
<tr class="odd">
<td><strong>Global physical</strong></td>
<td>Specify (in percent) the maximum system-wide virtual memory usage allowed before throttling begins.</td>
<td>0: disable<br />
<br />
1% – 100%<br />
<br />
Values &gt; 100% are treated as MBs and can go up to int Max</td>
<td>0</td>
</tr>
<tr class="even">
<td><strong>Process virtual</strong></td>
<td>Specify the maximum process memory (in percent) allowed before throttling begins (in percent or megabytes).</td>
<td>0: disable<br />
<br />
1% – 100%<br />
<br />
Values &gt; 100% are treated as MBs and can go up to int Max</td>
<td>25</td>
</tr>
<tr class="odd">
<td><strong>Spool multiplier</strong></td>
<td>Indicate the factor by which the <strong>Message count in DB</strong> threshold is multiplied and then compared against the current record count in the spool table.<br />
<br />
This is done to determine whether the system should throttle on spool table size. If this value is set to 0, spool table size is not used as a consideration for determining a throttling condition.</td>
<td>0-1000</td>
<td>10</td>
</tr>
<tr class="even">
<td><strong>Tracking data multiplier</strong></td>
<td>Specify the factor by which the <strong>Message count in DB</strong> threshold is multiplied and then compared against the current record count in the tracking table.<br />
<br />
This is done to determine whether the system should throttle on tracking table size. If this value is set to 0, tracking table size is not used as a consideration for determining a throttling condition.</td>
<td>0-1000</td>
<td>10</td>
</tr>
<tr class="odd">
<td><strong>Limit to trigger GC</strong></td>
<td>Specifies when a .NET garbage collection (GC) is triggered as process memory consumption increases and approaches the threshold. When the memory consumption exceeds this percentage value of the memory threshold, a GC is triggered.</td>
<td>50-100</td>
<td>80</td>
</tr>
<tr class="even">
<td><strong>Batch memory threshold</strong></td>
<td>Indicate (in percent) the memory threshold beyond which to throttle the publishing of a batch of messages.<br />
<br />
The batch memory threshold is computed by multiplying this percentage factor by the <strong>Process virtual</strong> threshold. If the memory estimated to execute a publishing batch exceeds the batch memory threshold, the batch is subject to process memory based throttling. Otherwise, the batch is exempted from process memory based throttling even when the total process memory exceeds the <strong>Process virtual</strong> threshold.<br />
<br />
A value of zero indicates that all publishing batches may be subject to process memory based throttling even if the memory estimated to execute the batch is minimal.</td>
<td>0%-100%</td>
<td>1</td>
</tr>
<tr class="odd">
<td><strong>Severity</strong></td>
<td></td>
<td>-</td>
<td>-</td>
</tr>
<tr class="even">
<td><strong>Memory</strong></td>
<td>Indicate the severity of a process memory triggered throttling condition. Specified in percentage value, this parameter sets the severity of a throttling condition caused when the <strong>Process virtual</strong> threshold is exceeded.</td>
<td>1 – 1000</td>
<td>500</td>
</tr>
<tr class="odd">
<td><strong>DB size</strong></td>
<td>Indicate the severity of a database sized triggered throttling condition. Specified in percentage value, this parameter sets the severity of a throttling condition caused when the <strong>Message count in DB</strong> threshold is exceeded.</td>
<td>1 – 1000</td>
<td>1</td>
</tr>
<tr class="even">
<td><strong>Inflight message</strong></td>
<td>Specify the reaction time of throttling when the value for <strong>In-process messages</strong> exceeds the threshold. This is specified in percentage value and this parameter sets the severity of a throttling condition caused when the value for <strong>In-process messages</strong> threshold is exceeded.</td>
<td>1 – 1000</td>
<td>75</td>
</tr>
<tr class="odd">
<td><strong>Restore Defaults</strong></td>
<td>Click to cancel the modifications done and apply the default BizTalk settings.</td>
<td>-</td>
<td>-</td>
</tr>
</tbody>
</table>


## See Also

[How to Modify Group Settings](https://msdn.microsoft.com/en-us/library/ff629808\(v=bts.80\))  
[How to Modify Host Instance Settings](https://msdn.microsoft.com/en-us/library/ff629695\(v=bts.80\))

