---
title: WCF-NetMsmq Transport Properties Dialog Box, Send, Binding Tab
TOCTitle: WCF-NetMsmq Transport Properties Dialog Box, Send, Binding Tab
ms:assetid: 52c6c522-cbb1-44fc-97a1-06e1106dcd76
ms:mtpsurl: https://msdn.microsoft.com/library/Bb246101(v=BTS.80)
ms:contentKeyID: 51528049
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netmsmq.transport.send.binding
---

# WCF-NetMsmq Transport Properties Dialog Box, Send, Binding Tab

 

Use the **Binding** tab to configure the binding properties specific to the WCF-NetMsmq send adapter. The WCF-NetMsmq adapter can communicate with a service through binary-encoded messages over the MSMQ transport. The WCF-NetMsmq adapter provides queued communication in a .NET-to-.NET environment.


> [!NOTE]
> <P>The current version of the WCF-NetMsmq adapter does not support WS-Reliable Messaging.</P>



<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Open timeout (hh:mmss)</strong></td>
<td>Specify a time span value that indicates the interval of time provided for a channel open operation to complete. This value should be greater than or equal to <strong>System.TimeSpan.Zero</strong>.<br />
<br />
Default value: 00:01:00<br />
<br />
Maximum value: 23:59:59</td>
</tr>
<tr class="even">
<td><strong>Send timeout (hh:mmss)</strong></td>
<td>Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to <strong>System.TimeSpan.Zero</strong>.<br />
<br />
Default value: 00:01:00<br />
<br />
Maximum value: 23:59:59</td>
</tr>
<tr class="odd">
<td><strong>Close timeout (hh:mmss)</strong></td>
<td>Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal to <strong>System.TimeSpan.Zero</strong>.<br />
<br />
Default value: 00:01:00<br />
<br />
Maximum value: 23:59:59</td>
</tr>
<tr class="even">
<td><strong>Transactional</strong></td>
<td>Specify the type of the message queue for the destination service: transactional or nontransactional. If this property is selected, each message processed by this send port is delivered only once, and the sender is notified of delivery failures. To send messages through transactional send ports, both the <strong>durable</strong> and <strong>exactlyOnce</strong> binding elements of the service must be set to <strong>true</strong>. If this property is cleared, messages are transferred without delivery assurance.<br />
<br />
The default value is selected.</td>
</tr>
<tr class="odd">
<td><strong>Message time to live (dd.hh:mm:ss)</strong></td>
<td>Specify a time span for how long the messages are valid before they are expired and put into the dead-letter queue. This property is set to ensure that time-sensitive messages do not become stale before they are processed by this send port. A message in a queue that is not consumed by this send port within the time interval specified is said to be expired. Expired messages are sent to special queue called the dead letter queue. The location of the dead letter queue is set with the <strong>Dead letter queue</strong> property..<br />
<br />
The default is 1.00:00:00</td>
</tr>
<tr class="even">
<td><strong>Use source journal queue</strong></td>
<td>Specify whether to copies of messages processed by this send port should be stored in the source journal queue.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Dead letter queue</strong></td>
<td>Specify the dead-letter queue where messages that have failed to be delivered to the application will be transferred. More information about the messages delivered to the dead letter queue is listed in the following section, &quot;Messages Delivered to the Dead Letter Queue.&quot;<br />
<br />
Valid values include the following:<br />
<br />
- <strong>None</strong>: No dead letter queue is to be used.<br />
- <strong>System</strong>: Use the system-wide dead letter queue.<br />
- <strong>Custom</strong>: Custom dead letter queue. <strong>Note:</strong> The custom dead-letter queue is supported only in Message Queuing (MSMQ) 4.0, released with Windows Vista.<br />
- The default is <strong>System</strong>.</td>
</tr>
<tr class="even">
<td><strong>Custom dead letter queue</strong></td>
<td>Specify the fully qualified URI with the <strong>net.msmq</strong> scheme for the location of the per-application dead letter queue, where messages that have expired or that have failed transfer or delivery are placed. For example, net.msmq://localhost/deadLetterQueueName. The dead letter queue is a queue on the queue manager of the sending application for expired messages that have failed to be delivered. This property is required if the <strong>Dead letter queue</strong> property is set to <strong>Custom</strong>.<br />
<br />
More information about the messages delivered to the dead letter queue is listed in the following section, &quot;Messages Delivered to the Dead Letter Queue.&quot;<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256<br />
<br />
The default is an empty string.</td>
</tr>
</tbody>
</table>


## Messages Delivered to the Dead Letter Queue

The dead-letter queue is a queue managed by the sending application's Queue Manager that stores messages that have failed to be delivered or have expired. The reasons that a message can fail to reach the receiving application include:

  - A transactional message is sent to a nontransactional queue.

  - A nontransactional message is sent to a transactional queue.

  - An unauthenticated message is sent to a queue that accepts only authenticated messages.

  - An unencrypted message is sent to a queue that accepts only encrypted messages.

  - The message expires before the message is delivered to a receiver.

  - The message storage quota of the target computer or the storage quota of the destination queue is exceeded, or there is no available storage space on the target computer when the message arrives.

  - The sender does not have the access rights needed to place the message in the destination queue.

  - The digital signature attached to the message is not valid.

  - An encrypted message cannot be decrypted by the destination queue manager.

  - The destination queue is purged or deleted before the message is retrieved.
    

    > [!NOTE]
    > <P>If the <STRONG>Dead letter queue</STRONG> property is set to <STRONG>None</STRONG>, messages can be lost if target queue service failure occurs. If the <STRONG>Dead letter queue</STRONG> property is set to <STRONG>System</STRONG>, failed messages are placed in the transactional dead-letter queue or nontransactional dead-letter queue depending on the <STRONG>Transactional</STRONG> property.</P>



## See Also

[How to Configure a WCF-NetMsmq Send Port](https://msdn.microsoft.com/library/bb245965\(v=bts.80\))  
[Sending and Retrieving Messages within a Transaction](http://go.microsoft.com/fwlink/?linkid=75752)

