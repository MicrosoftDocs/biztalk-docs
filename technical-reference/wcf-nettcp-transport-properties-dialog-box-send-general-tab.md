---
title: WCF-NetTcp Transport Properties Dialog Box, Send, General Tab
TOCTitle: WCF-NetTcp Transport Properties Dialog Box, Send, General Tab
ms:assetid: 505f4db5-3e1d-4e95-8bf3-e53f8c203737
ms:mtpsurl: https://msdn.microsoft.com/library/Bb246090(v=BTS.80)
ms:contentKeyID: 51527990
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-nettcp.transport.send.general
---

# WCF-NetTcp Transport Properties Dialog Box, Send, General Tab

 

Use the **General** tab to configure the endpoint address, the service identity, and the **SOAP Action** header for the WCF-NetTcp send port.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Address (URI)</strong></td>
<td>Required. Specify the fully qualified URI with the <strong>net.tcp</strong> scheme for this send port.<br />
<br />
Maximum length: 255<br />
<br />
Default value: net.tcp://localhost/</td>
</tr>
<tr class="even">
<td><strong>Endpoint Identity</strong></td>
<td>Optional. Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element. The values that can be specified for the <strong>Endpoint identity</strong> property differ according to the security configuration.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Action</strong></td>
<td>Specify the <strong>SOAPAction</strong> header field for outgoing messages. This property can also be set through the message context property <strong>WCF.Action</strong> in a pipeline or orchestration. You can specify this value in two different ways: the single action format and the action mapping format. If you set this property in the single action format- for example, http://contoso.com/Svc/Op1- the <strong>SOAPAction</strong> header for outgoing messages is always set to the value specified in this property.<br />
<br />
If you set this property in the action mapping format, the outgoing <strong>SOAPAction</strong> header is determined by the <strong>BTS.Operation</strong> context property. For example, if this property is set to the following XML format and the <strong>BTS.Operation</strong> property is set to Op1, the WCF send adapter uses http://contoso.com/Svc/Op1 for the outgoing <strong>SOAPAction</strong> header.<br />
<br />
&lt;BtsActionMapping&gt;<br />
<br />
&lt;Operation Name=&quot;Op1&quot; Action=&quot;http://contoso.com/Svc/Op1&quot; /&gt;<br />
<br />
&lt;Operation Name=&quot;Op2&quot; Action=&quot;http://contoso.com/Svc/Op2&quot; /&gt;<br />
<br />
&lt;/BtsActionMapping&gt;<br />
<br />
If outgoing messages come from an orchestration port, orchestration instances dynamically set the <strong>BTS.Operation</strong> property with the operation name of the port. If outgoing messages are routed with content-based routing, you can set the <strong>BTS.Operation</strong> property in pipeline components.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is an empty string.</td>
</tr>
</tbody>
</table>


## See Also

[The \<identity\> element](http://go.microsoft.com/fwlink/?linkid=75747)  
[How to Configure a WCF-NetTcp Send Port](https://msdn.microsoft.com/library/bb226460\(v=bts.80\))  
[WCF Adapters Property Schema and Properties](https://msdn.microsoft.com/library/bb245991\(v=bts.80\))  
[Configuring Dynamic Send Ports Using WCF Adapters Context Properties](https://msdn.microsoft.com/library/bb727706\(v=bts.80\))

