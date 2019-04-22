---
title: WCF-Custom Transport Properties Dialog Box, Send, General Tab
TOCTitle: WCF-Custom Transport Properties Dialog Box, Send, General Tab
ms:assetid: dd6f0eae-eb8b-4e1c-ad92-e101942fc0b1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb226568(v=BTS.80)
ms:contentKeyID: 51532799
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-custom.transport.send.general
---

# WCF-Custom Transport Properties Dialog Box, Send, General Tab

 

Use the **General** tab to configure the endpoint address, the service identity, and the SOAP **Action** feature for the WCF-Custom send port. The WCF-Custom adapter enables the use of Windows Communication Foundation (WCF) extensibility features. The adapter allows users to select and configure a WCF binding, behavior, and behavior extensions for the receive location and send port.

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
<td>Required. Specify the fully qualified URI of the destination service for this send port. The available transport scheme for this property is decided by the <strong>Binding Type</strong> property on the <strong>Binding</strong> tab. <strong>Note:</strong> You can also import and export this property through the <strong>Import/Export</strong> tab.<br />
<br />
Maximum length: 255<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Endpoint Identity</strong></td>
<td>Optional. Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the WCF infrastructure will ensure that the identity of the expected service matches the values of this element. The values that can be specified for the <strong>Endpoint Identity</strong> property differ according to the security configuration. <strong>Note:</strong> You can also import and export this property through the <strong>Import/Export</strong> tab. If the send port is configured to use multiple identity types, only the identity type with the lowest number can be exported. For example, if <strong>1. DNS</strong> and <strong>4. RSA</strong> are both set in the <strong>Identity Editor</strong> dialog box, only the <strong>1. DNS</strong> property is saved by using the <strong>Export</strong> tab.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Action</strong></td>
<td>Required. Specify the <strong>SOAPAction</strong> header field for outgoing messages. This property can also be set through the message context property <strong>WCF.Action</strong> in a pipeline or orchestration. You can specify this value in two different ways: the single action format and the action mapping format. If you set this property in the single action format- for example, http://contoso.com/Svc/Op1- the <strong>SOAPAction</strong> header for outgoing messages is always set to the value specified in this property.<br />
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
If outgoing messages comes from an orchestration port, orchestration instances dynamically set the <strong>BTS.Operation</strong> property with the operation name of the port. If outgoing messages are routed with content-based routing, you can set the <strong>BTS.Operation</strong> property in pipeline components.<br />
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

[How to Configure a WCF-Custom Send Port](https://msdn.microsoft.com/library/bb226446\(v=bts.80\))  
[WCF Adapters Property Schema and Properties](https://msdn.microsoft.com/library/bb245991\(v=bts.80\))  
[The \<identity\> element](http://go.microsoft.com/fwlink/?linkid=75747)  
[Configuring Dynamic Send Ports Using WCF Adapters Context Properties](https://msdn.microsoft.com/library/bb727706\(v=bts.80\))

