---
description: "Learn more about: MSMQ Transport Properties Dialog Box, Receive"
title: MSMQ Transport Properties Dialog Box, Receive
TOCTitle: MSMQ Transport Properties Dialog Box, Receive
ms:assetid: 890a00b2-deca-412f-853e-85816c3f0c0d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561241(v=BTS.80)
ms:contentKeyID: 51529506
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.msmq.transport.receive
---

# MSMQ Transport Properties Dialog Box, Receive

 

Use the **MSMQ Transport Properties** dialog box to configure the receive location properties for the MSMQ adapter.

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
<td>Set a password to use for a remote queue.</td>
</tr>
<tr class="even">
<td><strong>User Name</strong></td>
<td>Determine the user name to use, in combination with the password, for access to a remote queue. You cannot use the local user of the remote computer for the user name.</td>
</tr>
<tr class="odd">
<td><strong>Batch Size</strong></td>
<td>Configure the batch size using this property. BizTalk 2006 Adapter for MSMQ submits messages to the MessageBox database in batches. The default batch size is 0, and the minimum batch size is 1. <strong>Note:</strong> If the <strong>Transactional</strong> property for the receive location is set to <strong>True</strong>; each message batch is submitted to the MessageBox database under the context of a Microsoft Distributed Transaction Coordinator (MSDTC) transaction. The MSDTC transaction that is created for a message batch remains open until every message in the batch has been persisted to the MessageBox and placed in the appropriate subscriber queue. Therefore the duration of this MSDTC transaction is increased as the <strong>Batch Size</strong> parameter is increased. Since having a large number of MSDTC transactions open simultaneously can negatively impact overall performance, the <strong>Batch Size</strong> parameter should not be set to a very large value when transaction support is enabled.</td>
</tr>
<tr class="even">
<td><strong>Queue</strong></td>
<td>Type a valid queue path. Depending on the queue path you specify, the system performs the appropriate validations.</td>
</tr>
<tr class="odd">
<td><strong>On Failure</strong></td>
<td>Specify how the adapter should respond to an error. Set this property to one of the following values:<br />
<br />
Stop. Stop receiving messages through this receive location if an error condition occurs.<br />
<br />
Suspend(non-resumable). Suspend messages and mark as non-resumable.<br />
<br />
Suspend(resumable). Suspend messages and mark as resumable. <strong>Important:</strong> If the True option for Ordered Processing property, the Stop option for the On Failure property, and the False option for the Transactional property are applied at the same time, then any messages that fail delivery will not be suspended or left in the source queue. In this scenario, message loss can occur. To prevent data loss, when using the Ordered Processing feature, the Stop option for the On Failure property should only be applied if the True option for the Transactional property is applied. Then, if a message delivery failure occurs, the original message will be left in the source MSMQ queue. If the Ordered Processing property is set to a value of False then the On Failure property will not take effect and if a message delivery failure occurs the message will be suspended with a status of Suspended (resumable).</td>
</tr>
<tr class="even">
<td><strong>Ordered processing</strong></td>
<td>Set this property to True or False. This indicates whether to process messages serially. Setting the property to True will accommodate ordered message delivery when used in conjunction with a BizTalk Messaging or Orchestration Send Port that has the Ordered Delivery option set to True. For more information about the Ordered Delivery option, see the appropriate topics in See Also.<br />
<br />
Setting this property to True also optimizes resource usage when handling large messages by making the adapter single-threaded. For more information about sending and receiving large messages, see the appropriate topics in See Also.</td>
</tr>
<tr class="odd">
<td><strong>Transactional</strong></td>
<td>Set this property to True or False. <strong>Note:</strong> The adapter does not support transactional reads on remote queues.<br />
<br />
For more information about configuring the MSMQ adapter properties and running adapters within a clustered host, see the appropriate topics in See Also.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure an MSMQ Receive Location](https://msdn.microsoft.com/library/aa578322\(v=bts.80\))  
[Ordered Delivery of Messages](https://msdn.microsoft.com/library/aa559637\(v=bts.80\))  
[Sending and Receiving Large Messages Using the MSMQ Adapter](https://msdn.microsoft.com/library/aa559149\(v=bts.80\))  
[Considerations for Running Adapter Handlers within a Clustered Host](https://msdn.microsoft.com/library/aa561801\(v=bts.80\))

