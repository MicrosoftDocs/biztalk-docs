---
description: "Learn more about: WCF-WSHttp Transport Properties Dialog Box, Send, Binding Tab"
title: WCF-WSHttp Transport Properties Dialog Box, Send, Binding Tab
TOCTitle: WCF-WSHttp Transport Properties Dialog Box, Send, Binding Tab
ms:assetid: 2093e122-91db-47e5-a970-46e03339e934
ms:mtpsurl: https://msdn.microsoft.com/library/Bb245992(v=BTS.80)
ms:contentKeyID: 51526743
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-wshttp.transport.send.binding
---

# WCF-WSHttp Transport Properties Dialog Box, Send, Binding Tab

 

Use the **Binding** tab to configure the binding properties specific to the WCF-WSHttp send adapter. The WCF-WSHttp adapter can communicate with a service through the WS-\* standards over HTTP and HTTPS.


> [!NOTE]
> <P>The current version of the WCF-WSHttp adapter does not support WS-Reliable Messaging.</P>



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
Default value: 65536<br />
<br />
Maximum value: 2147483647</td>
</tr>
<tr class="odd">
<td><strong>Message encoding</strong></td>
<td>Specify the encoder used to encode the SOAP message. Valid values include the following:<br />
<br />
- <strong>Text</strong>: Use a text message encoder.<br />
- <strong>Mtom</strong>: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.<br />
<br />
The default is <strong>Text</strong>.</td>
</tr>
<tr class="even">
<td><strong>Text encoding</strong></td>
<td>Specify the character set encoding to be used for emitting messages on the binding when the <strong>Message encoding</strong> property is set to <strong>Text</strong>. Valid values include the following:<br />
<br />
- <strong>utf-16BE (unicodeFFFE)</strong>: Unicode BigEndian encoding.<br />
- <strong>utf-16</strong>: 16-bit encoding.<br />
- <strong>utf-8</strong>: 8-bit encoding<br />
<br />
The default is <strong>utf-8</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Enable transactions</strong></td>
<td>Specify whether a message is transmitted to the destination service and deleted from the MessageBox database in a transactional context using the <strong>WS-AtomicTransaction</strong> protocol.<br />
<br />
The default value is cleared.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-WSHttp Send Port](https://msdn.microsoft.com/library/bb245939\(v=bts.80\))

