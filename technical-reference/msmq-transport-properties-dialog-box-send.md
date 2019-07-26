---
title: MSMQ Transport Properties Dialog Box, Send
TOCTitle: MSMQ Transport Properties Dialog Box, Send
ms:assetid: bd8061c0-ee26-4ccb-9862-274abf6f10f5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578385(v=BTS.80)
ms:contentKeyID: 51530968
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.msmq.transport.send
---

# MSMQ Transport Properties Dialog Box, Send

 

Use the **MSMQ Transport Properties** dialog box to configure the send port properties for the MSMQ adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the password for a remote queue. Use with User Name.</td>
</tr>
<tr class="even">
<td><strong>User Name</strong></td>
<td>Specify the user name for a remote queue. Use with Password. You cannot use the local user of the remote computer for the user name.</td>
</tr>
<tr class="odd">
<td><strong>Acknowledgement Type</strong></td>
<td>Specify the type of acknowledgement message for Message Queuing to return to the sending application. You can check more than one acknowledgment type. Any of the acknowledgement types in the System.Messaging.AcknowledgeTypes enumeration are available.</td>
</tr>
<tr class="even">
<td><strong>Administration Queue</strong></td>
<td>Specify the queue name that receives the acknowledgement message. You must specify a value for the Administration Queue if you specify a value for the Acknowledgement Type.</td>
</tr>
<tr class="odd">
<td><strong>Body Type</strong></td>
<td>Specify the message body type in MSMQ. Valid values are members of the .NET VarEnum enumeration.</td>
</tr>
<tr class="even">
<td><strong>Certificate Thumbprint</strong></td>
<td>Specify the thumbprint of the certificate to use for message authentication. Use this property in combination with the Use Authentication property to verify the message. Use the User Name and Password properties to gain access to queues.</td>
</tr>
<tr class="odd">
<td><strong>Destination Queue</strong></td>
<td>Specify the destination queue. For more information about queues, see the appropriate topics in See Also.</td>
</tr>
<tr class="even">
<td><strong>Encryption Algorithm</strong></td>
<td>Select RC2, RC4, or None for the encryption algorithm.</td>
</tr>
<tr class="odd">
<td><strong>Maximum Message Size (in kilobytes)</strong></td>
<td>Specify the maximum message size for messages that you send to the specified queue.</td>
</tr>
<tr class="even">
<td><strong>Message Priority</strong></td>
<td>Set the message priority.</td>
</tr>
<tr class="odd">
<td><strong>Recoverable</strong></td>
<td>Specify whether to guarantee if a message is recoverable.</td>
</tr>
<tr class="even">
<td><strong>Support Segmentation</strong></td>
<td>Set this Boolean property value to True to segment messages larger than 4 MB.</td>
</tr>
<tr class="odd">
<td><strong>Timeout</strong></td>
<td>Specify the maximum time to wait for the messages to reach the destination queue. Applies only when you use transactions.</td>
</tr>
<tr class="even">
<td><strong>Timeout Unit</strong></td>
<td>Set the unit to use for the Timeout property.<br />
<br />
Select Days, Hours, Minutes, or Seconds.</td>
</tr>
<tr class="odd">
<td><strong>Transactional</strong></td>
<td>Set this value to True to send messages if you use transactions.</td>
</tr>
<tr class="even">
<td><strong>Use Authentication</strong></td>
<td>Set this Boolean property value to True to control authentication. Use this property in combination with the Certificate Thumbprint property to verify the message. Use the User Name and Password properties to gain access to queues.</td>
</tr>
<tr class="odd">
<td><strong>Use Dead Letter Queue</strong></td>
<td>Set this value to True to send messages to the dead letter queue if a failure occurs.</td>
</tr>
<tr class="even">
<td><strong>Use Journal Queue</strong></td>
<td>Set this value to True to save a copy of the message whenever the message is processed.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure an MSMQ Send Port](https://msdn.microsoft.com/library/aa559595\(v=bts.80\))  
[Message Queuing Queues](https://msdn.microsoft.com/library/aa578285\(v=bts.80\))

