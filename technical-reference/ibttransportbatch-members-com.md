---
title: IBTTransportBatch Members (COM)
TOCTitle: IBTTransportBatch Members (COM)
ms:assetid: 59bb0b1f-6599-426b-858b-ddf2bd733d26
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560303(v=BTS.80)
ms:contentKeyID: 51528229
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IBTTransportBatch Members (COM)

 

[IBTTransportBatch overview](ibttransportbatch-interface-com.md)

## Public Properties

<table>
<tbody>
<tr class="odd">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" /> <a href="ibttransportbatch-resourcetracker-property-com.md">ResourceTracker</a></td>
<td>This property is not supported and returns a value of E_NOTIMPL.</td>
</tr>
</tbody>
</table>


## Public Methods

<table>
<tbody>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransportbatch-cancelresponsemessage-method-com.md">CancelResponseMessage</a></td>
<td>Adds a cancellation request to the batch to cancel a request for a response message.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransportbatch-clear-method-com.md">Clear</a></td>
<td>Clears the batch.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransportbatch-deletemessage-method-com.md">DeleteMessage</a></td>
<td>Adds a message to the batch to be deleted.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransportbatch-done-method-com.md">Done</a></td>
<td>Posts the batch of work to the thread pool for the BizTalk Server Messaging Engine where it will be processed asynchronously.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransportbatch-movetonexttransport-method-com.md">MoveToNextTransport</a></td>
<td>Adds a message to the batch to be moved to the backup transport.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransportbatch-movetosuspendq-method-com.md">MoveToSuspendQ</a></td>
<td>Adds a message to the batch to be suspended.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransportbatch-resubmit-method-com.md">Resubmit</a></td>
<td>Adds a message to the batch to be resubmitted.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransportbatch-submitmessage-method-com.md">SubmitMessage</a></td>
<td>Adds a message to the batch to be processed by the BizTalk Server Messaging Engine.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransportbatch-submitrequestmessage-method-com.md">SubmitRequestMessage</a></td>
<td>Submits a request message for a request-response pair.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransportbatch-submitresponsemessage-method-com.md">SubmitResponseMessage</a></td>
<td>Submits the response message for a solicit-response pair.</td>
</tr>
</tbody>
</table>


## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)

