---
title: IBTTransmitterBatch Methods (COM)
TOCTitle: IBTTransmitterBatch Methods (COM)
ms:assetid: 59f297d0-bc25-43cd-a92f-aecf9197c0f3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560309(v=BTS.80)
ms:contentKeyID: 51528250
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IBTTransmitterBatch Methods (COM)

 

The methods of the **IBTTransmitterBatch** interface are listed here. For a complete list of **IBTTransmitterBatch** interface members, see the [IBTTransmitterBatch Members](ibttransmitterbatch-members-com.md) topic.

## Public Methods

<table>
<tbody>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransmitterbatch-beginbatch-method-com.md">BeginBatch</a></td>
<td>Initializes the batch.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransmitterbatch-clear-method-com.md">Clear</a></td>
<td>Clears the batch if one or more calls to the <a href="ibttransmitterbatch-transmitmessage-method-com.md">TransmitMessage</a> method failed.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransmitterbatch-done-method-com.md">Done</a></td>
<td>Indicates that either the batch is full or the BizTalk Server Messaging Engine does not have any more messages for this batch.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibttransmitterbatch-transmitmessage-method-com.md">TransmitMessage</a></td>
<td>Adds messages to the adapter batch that are ready to be transmitted.</td>
</tr>
</tbody>
</table>


## See Also

[IBTTransmitterBatch Interface (COM)](ibttransmitterbatch-interface-com.md)

