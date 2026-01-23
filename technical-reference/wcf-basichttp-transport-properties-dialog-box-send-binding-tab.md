---
description: "Learn more about: WCF-BasicHttp Transport Properties Dialog Box, Send, Binding Tab"
title: WCF-BasicHttp Transport Properties Dialog Box, Send, Binding Tab
TOCTitle: WCF-BasicHttp Transport Properties Dialog Box, Send, Binding Tab
ms:assetid: faf38378-34b5-4282-ba86-3c72ba610451
ms:mtpsurl: https://msdn.microsoft.com/library/Bb259980(v=BTS.80)
ms:contentKeyID: 51533583
ms.date: 08/30/2017
ms.topic: ui-reference
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-basichttp.transport.send.binding
---

# WCF-BasicHttp Transport Properties Dialog Box, Send, Binding Tab

 

Use the **Binding** tab to configure the binding properties specific to WCF-BasicHttp send adapter. The WCF-BasicHttp adapter can communicate with WS-I Basic Profile 1.1-conformant Web services like ASMX-based services.

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
<td>Specify a time span value that indicates the interval of time provided for a channel close operation to complete. This value should be greater than or equal <strong>System.TimeSpan.Zero</strong>.<br />
<br />
Default value: 00:01:00<br />
<br />
Maximum value: 23:59:59</td>
</tr>
<tr class="even">
<td><strong>Maximum received message size (bytes)</strong></td>
<td>Specify the maximum size, in bytes, for a message including headers, which can be received on the wire. The size of the messages is bounded by the amount of memory allocated for each message. You can use this property to limit exposure to denial of service (DoS) attacks.<br />
<br />
The WCF-BasicHttp adapter leverages the <a href="/dotnet/api/system.servicemodel.basichttpbinding">BasicHttpBinding</a> class in the buffered transfer mode to communicate with an endpoint. For the buffered transport mode, the <a href="/dotnet/api/system.servicemodel.basichttpbinding.maxbuffersize">BasicHttpBinding.MaxBufferSize</a> property is always equal to the value of this property.<br />
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
Default value: <strong>Text</strong></td>
</tr>
<tr class="even">
<td><strong>Text encoding</strong></td>
<td>Specify the character set encoding to be used for emitting messages on the binding when the <strong>Message encoding</strong> property is set to <strong>Text</strong>. Valid values include the following:<br />
<br />
- <strong>utf-16BE (unicodeFFFE)</strong>: Unicode BigEndian encoding.<br />
- <strong>utf-16</strong>: 16-bit encoding.<br />
- <strong>utf-8</strong>: 8-bit encoding<br />
<br />
Default value: <strong>utf-8</strong></td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-BasicHttp Send Port](https://msdn.microsoft.com/library/bb226467\(v=bts.80\))