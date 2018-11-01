---
title: WCF-NetMsmq Transport Properties Dialog Box, Receive, Binding Tab
TOCTitle: WCF-NetMsmq Transport Properties Dialog Box, Receive, Binding Tab
ms:assetid: 183a2a54-ddde-44b1-891b-76a30eb21146
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb245972(v=BTS.80)
ms:contentKeyID: 51526466
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netmsmq.transport.receive.binding
---

# WCF-NetMsmq Transport Properties Dialog Box, Receive, Binding Tab

 

Use the **Binding** tab to define the binding properties specific to the WCF-NetMsmq receive adapter. The WCF-NetMsmq receive adapter can use to communicate with a service through binary-encoded messages over the MSMQ transport. The WCF-NetMsmq adapter provides queued communication in a .NET-to-.NET environment.

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
<td><strong>Maximum received message size (bytes)</strong></td>
<td>Specify the maximum size, in bytes, for a message including headers, which can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br />
<br />
Default value: 65536<br />
<br />
Maximum value: 2147483647</td>
</tr>
<tr class="odd">
<td><strong>Transactional</strong></td>
<td>Specify the type of message queue: transactional or nontransactional. If this property is selected, each message is delivered only once, and the sender is notified of delivery failures. To send messages through transactional send ports, both the <strong>durable</strong> and <strong>exactlyOnce</strong> binding elements of the client must be set to <strong>true</strong>. If this property is cleared, messages are transferred without delivery assurance. <strong>Note:</strong> If you use a transactional queue under this receive location, this property must be selected. <strong>Note:</strong> ReplaceThisText<br />
<br />
The default value is selected.</td>
</tr>
<tr class="even">
<td><strong>Ordered processing</strong></td>
<td>Specify whether to process messages serially. When this property is selected, this receive location accommodates ordered message delivery when used in conjunction with a BizTalk messaging or orchestration send port that has the <strong>Ordered Delivery</strong> option set to <strong>True</strong>. You can select this only when the <strong>Transaction</strong> property is selected.<br />
<br />
For more information about the Ordered Delivery option, see the appropriate topics in See Also.<br />
<br />
Selecting this property also optimizes resource usage when handling large messages by making the adapter single-threaded. For more information about sending and receiving large messages, see the appropriate topics in See Also.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Maximum concurrent calls</strong></td>
<td>Specify the number of concurrent calls to a single service instance. Calls in excess of the limit are queued. Setting this value to 0 is equivalent to setting it to <strong>Int32.MaxValue</strong>.<br />
<br />
Default value: 200</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-NetMsmq Receive Location](https://msdn.microsoft.com/en-us/library/bb259976\(v=bts.80\))  
[Ordered Delivery of Messages](https://msdn.microsoft.com/en-us/library/aa559637\(v=bts.80\))  
[Sending and Retrieving Messages within a Transaction](http://go.microsoft.com/fwlink/?linkid=75752)

