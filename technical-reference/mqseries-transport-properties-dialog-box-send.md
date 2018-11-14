---
title: MQSeries Transport Properties Dialog Box, Send
TOCTitle: MQSeries Transport Properties Dialog Box, Send
ms:assetid: 5a9ae8e2-9d5c-411e-b9b6-7f625c26a082
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560320(v=BTS.80)
ms:contentKeyID: 51528254
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.mqseries.transport.send
---

# MQSeries Transport Properties Dialog Box, Send

 

Use the **MQSeries Transport Properties** dialog box to configure send port for the MQSeries adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Fragmentation Size</strong></td>
<td>Sets the message chunk size in KB for messages as they are sent between the adapter and MQSAgent.</td>
</tr>
<tr class="even">
<td><strong>SSO Affiliate Application</strong></td>
<td>Sets the Single Sign-On (SSO) affiliate application. The user ID and password from SSO are used for the MQMD_UserIdentifier, and the MQIIH_Authenticator (or MQCIH_Authenticator) property, respectively.<br />
<br />
Default: Blank</td>
</tr>
<tr class="odd">
<td><strong>Data Conversion</strong></td>
<td>Converts the message to the ANSI code page of MQSeries for Windows Server.<br />
<br />
Select Yes to perform this conversion from Unicode to ANSI.<br />
<br />
Default: No</td>
</tr>
<tr class="even">
<td><strong>Ordered</strong></td>
<td>Sets MQSeries to maintain the order of messages as they are sent to the MQSeries queue.<br />
<br />
Select Yes to maintain message order. <strong>Note:</strong> You must set the Delivery Notification property in your orchestration to Transmitted for the send port.<br />
<br />
Default: No</td>
</tr>
<tr class="odd">
<td><strong>Queue Definition</strong></td>
<td>Populated with information from the Queue Definition dialog box or directly in the field.</td>
</tr>
<tr class="even">
<td><strong>Segmentation Allowed</strong></td>
<td>Uses MQSeries Queue Manager segmentation if an individual message exceeds the MQSeries queue maximum message length. If you select Yes, MQSeries puts segmented messages into the queue.<br />
<br />
Default: No</td>
</tr>
<tr class="odd">
<td><strong>Transaction Supported</strong></td>
<td>The adapter begins a Distributed Transaction Coordinator (DTC) transaction between BizTalk Server and MQSeries server. When set to No, there is no guarantee of message delivery.<br />
<br />
Default: Yes</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure MQSeries Adapter Receive Locations and Send Ports](https://msdn.microsoft.com/library/aa560215\(v=bts.80\))

