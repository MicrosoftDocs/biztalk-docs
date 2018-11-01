---
title: WCF-NetNamedPipe Transport Properties Dialog Box, Receive, Binding Tab
TOCTitle: WCF-NetNamedPipe Transport Properties Dialog Box, Receive, Binding Tab
ms:assetid: f47fa4ec-260e-4224-b645-623c735167e8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb259971(v=BTS.80)
ms:contentKeyID: 51533416
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netnamedpipe.transport.receive.binding
---

# WCF-NetNamedPipe Transport Properties Dialog Box, Receive, Binding Tab

 

Use the **Binding** tab to define the binding properties specific to the WCF-NetNamedPipe receive adapter. The WCF-NetNamedPipe adapter provides efficient cross-process communication in a .NET-to-.NET environment. The adapter uses the named pipe transport and messages have a binary encoding. This adapter cannot be used in cross-computer communication.


> [!NOTE]
> <P>The current version of the WCF-NetNamedPipe adapter does not support WS-Reliable Messaging.</P>



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
<td>Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to <strong>System.TimeSpan.Zero</strong>. If you use a request-response receive port, this value specifies a time span for the whole interaction to complete, even if the client returns a large message.<br />
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
<td><strong>Enable transactions</strong></td>
<td>Specify whether a message is submitted to the MessageBox database using the transaction flowed from clients. If this property is set, the clients are required to submit messages using the transaction protocol specified in the <strong>Transaction protocol</strong> property. If the clients submit messages outside the transactional scope then this receive location returns an exception back to the clients, and no messages are suspended.<br />
<br />
The option is available only for one-way receive locations. If the clients submit messages in a transactional context for request-response receive locations, then an exception is returned back to the clients and no messages are suspended.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="even">
<td><strong>Transaction protocol</strong></td>
<td>Specify the transaction protocol to be used with this binding. Valid values include the following:<br />
<br />
- <strong>OleTransaction</strong><br />
- <strong>WS-AtomicTransaction</strong><br />
<br />
The default is <strong>OleTransaction</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Maximum concurrent calls</strong></td>
<td>Specify the number of concurrent calls to a single service instance. Calls in excess of the limit are queued. Setting this value to 0 is equivalent to setting it to <strong>Int32.MaxValue</strong>.<br />
<br />
Default value: 200</td>
</tr>
</tbody>
</table>


## Transaction Semantics on Message Failures

The following table describes the semantics of transactional message submission on message failures during inbound processing:

<table>
<thead>
<tr class="header">
<th>Message submission result</th>
<th>Is the message suspended on failure?</th>
<th>Vote on the transaction outcome</th>
<th>Return result</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Failure</td>
<td>Yes</td>
<td>Commit</td>
<td>Error</td>
</tr>
<tr class="even">
<td>Failure</td>
<td>No</td>
<td>Abort</td>
<td>Error</td>
</tr>
<tr class="odd">
<td>Success</td>
<td>Yes</td>
<td>Commit</td>
<td>Success</td>
</tr>
<tr class="even">
<td>Success</td>
<td>No</td>
<td>Commit</td>
<td>Success</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-NetNamedPipe Receive Location](https://msdn.microsoft.com/en-us/library/bb259943\(v=bts.80\))

