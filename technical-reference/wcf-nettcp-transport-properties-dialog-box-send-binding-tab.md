---
title: WCF-NetTcp Transport Properties Dialog Box, Send, Binding Tab
TOCTitle: WCF-NetTcp Transport Properties Dialog Box, Send, Binding Tab
ms:assetid: ca2f3b64-d646-475e-a745-e767e39e6941
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb226527(v=BTS.80)
ms:contentKeyID: 51531176
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-nettcp.transport.send.binding
---

# WCF-NetTcp Transport Properties Dialog Box, Send, Binding Tab

 

Use the **Binding** tab to configure the binding properties specific to the WCF-NetTcp send adapter. The WCF-NetTcp adapter can communicate with a service through the WS-\* standards over the TCP transport, using messages that have a binary encoding.


> [!NOTE]
> <P>The current version of the WCF-NetTcp adapter does not support WS-Reliable Messaging.</P>



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
<td>Specify a time span value that indicates the interval of time provided for a send operation to complete. This value should be greater than or equal to <strong>System.TimeSpan.Zero</strong>. If you use a solicit-response send port, this value specifies a time span for the whole interaction to complete, even if the service returns a large message.<br />
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
The WCF-NetTcp adapter leverages the <a href="http://go.microsoft.com/fwlink/?linkid=81087">NetTcpBinding</a> class in the buffered transfer mode to communicate with an endpoint. For the buffered transport mode, the <a href="http://go.microsoft.com/fwlink/?linkid=81088">NetTcpBinding.MaxBufferSize</a> property is always equal to the value of this property.<br />
<br />
Default value: 65536<br />
<br />
Maximum value: 2147483647</td>
</tr>
<tr class="odd">
<td><strong>Enable transactions</strong></td>
<td>Specify whether a message is transmitted to the destination service and deleted from the MessageBox database in a transactional context using the transaction protocol specified in the <strong>Transaction protocol</strong> property.<br />
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
</tbody>
</table>


## See Also

[How to Configure a WCF-NetTcp Send Port](https://msdn.microsoft.com/library/bb226460\(v=bts.80\))

