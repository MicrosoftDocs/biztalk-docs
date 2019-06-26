---
title: MQSeries Transport Properties Dialog Box, Receive
TOCTitle: MQSeries Transport Properties Dialog Box, Receive
ms:assetid: 9518d873-f0f7-41e3-adbe-75f6be97a23a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577420(v=BTS.80)
ms:contentKeyID: 51529793
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.mqseries.transport.receive
---

# MQSeries Transport Properties Dialog Box, Receive

 

Use the **MQSeries Transport Properties** dialog box to configure the receive location properties for the MQSeries adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Event Log Error Threshold</strong></td>
<td>Determine the maximum number of errors to log. The adapter continues operating and, if the adapter recovers, it logs the event in the event log.</td>
</tr>
<tr class="even">
<td><strong>Fragmentation Size</strong></td>
<td>Set the message chunk size in KB for messages as they are sent between MQSAgent and the adapter.</td>
</tr>
<tr class="odd">
<td><strong>Maximum Batch Size</strong></td>
<td>Determine the maximum size of a batch of messages in KB. <strong>Note:</strong> If the <strong>Transaction Supported</strong> property for the receive location is set to <strong>Yes</strong>; each message batch is submitted to the MessageBox database under the context of a Microsoft Distributed Transaction Coordinator (MSDTC) transaction. The MSDTC transaction that is created for a message batch remains open until every message in the batch has been persisted to the MessageBox and placed in the appropriate subscriber queue. Therefore the duration of this MSDTC transaction is increased as the <strong>Maximum Batch Size</strong> parameter is increased. Since having a large number of MSDTC transactions open simultaneously can negatively impact overall performance, the <strong>Maximum Batch Size</strong> parameter should not be set to a very large value when transaction support is enabled.</td>
</tr>
<tr class="even">
<td><strong>Maximum Messages in Batch</strong></td>
<td>The maximum number of messages from 1 through 10,000 in a batch.</td>
</tr>
<tr class="odd">
<td><strong>Polling Interval</strong></td>
<td>Set the time interval from 0 to infinity used by the receive component to poll the MQSeries queue.<br />
<br />
The Polling Interval works in combination with the hard-coded wait interval of three seconds built into the adapter. If the Polling Interval value is less than 3 seconds, the wait interval is set to the value of the Polling Interval.</td>
</tr>
<tr class="even">
<td><strong>Polling Unit</strong></td>
<td>Set the unit of time for the polling interval.<br />
<br />
Default: Seconds</td>
</tr>
<tr class="odd">
<td><strong>Threads</strong></td>
<td>Establish the number of threads used per receive location.</td>
</tr>
<tr class="even">
<td><strong>Character Set</strong></td>
<td>Determine the character set and whether MQSeries converts characters before sending the message to the receive location:<br />
<br />
- None. Do not convert. UCS-2 and UTF-16. Convert to these character sets. MQSeries does not distinguish between them.<br />
- UTF-8. Convert to the UTF-8 character set.<br />
<br />
Default: None</td>
</tr>
<tr class="odd">
<td><strong>Data Offset for Headers</strong></td>
<td>The adapter uses values from the MQSeries headers (the MQXQH, MQIIH, and MQCIH structures) to populate corresponding values in the BizTalk Server context properties. By default, the adapter removes these MQSeries properties from the message body. Set this property to No to retain the properties in the message body.<br />
<br />
Default: Yes</td>
</tr>
<tr class="even">
<td><strong>Ordered</strong></td>
<td>Set MQSeries to maintain the order of the messages as they are received from the MQSeries queue.<br />
<br />
Select No Ordering to disregard message order.<br />
<br />
Select No Ordering with stop to disregard message order and to disable the receive location if there is an error.<br />
<br />
Use Order with Stop to enable ordering. This option ends the transaction and disables the receive location if there is an error.<br />
<br />
Use Order with Suspend to enable ordering. This option moves the message to the suspended queue when there is an error. This value does not preserve order when there is an error, but does allow the receive location to continue receiving messages. <strong>Note:</strong> To maintain message ordering for a specific queue, only one BizTalk Server host instance may be receiving messages from that MQSeries queue. <strong>Note:</strong> You must also set the Ordered Delivery property to True in your orchestration for this receive location. <strong>Note:</strong> Enabling ordered delivery will accommodate ordered message delivery when used in conjunction with a BizTalk Messaging or Orchestration Send Port that has the Ordered Delivery option set to True. For more information about the Ordered Delivery option, see the appropriate topics under See Also.<br />
<br />
Default: No Ordering</td>
</tr>
<tr class="odd">
<td><strong>Queue Definition</strong></td>
<td>Filled in with information from the Queue Definition dialog box.</td>
</tr>
<tr class="even">
<td><strong>Segmentation</strong></td>
<td>Set MQSeries to assemble segmented messages or to get the message as is. Use No Action to read messages from the MQSeries queue without enabling segmentation. Use Complete Message to have MQSeries assemble segmented messages before passing them on to the adapter.<br />
<br />
Default: No Action</td>
</tr>
<tr class="odd">
<td><strong>Suspend As Non Resumable</strong></td>
<td>Specify whether suspended messages are marked as resumable or not.<br />
<br />
Default: No</td>
</tr>
<tr class="even">
<td><strong>Transaction Supported</strong></td>
<td>The adapter begins a Distributed Transaction Coordinator (DTC) transaction between BizTalk Server and MQSeries server. When set to No, there is no guarantee of message delivery.<br />
<br />
Default: Yes</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure MQSeries Adapter Receive Locations and Send Ports](https://msdn.microsoft.com/library/aa560215\(v=bts.80\))  
[Ordered Delivery of Messages](https://msdn.microsoft.com/library/aa559637\(v=bts.80\))

