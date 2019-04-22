---
title: WCF-Custom Transport Properties Dialog Box, Receive, General Tab
TOCTitle: WCF-Custom Transport Properties Dialog Box, Receive, General Tab
ms:assetid: eef3d8c6-f79e-49de-b6d4-0d5a41d4463f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb259963(v=BTS.80)
ms:contentKeyID: 51533289
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-custom.transport.receive.general
---

# WCF-Custom Transport Properties Dialog Box, Receive, General Tab

 

Use the **General** tab to configure the endpoint address, and the service identity for the WCF-Custom and WCF-CustomIsolated receive locations.

The WCF-Custom adapter enables the use of Windows Communication Foundation (WCF) extensibility features. The WCF-Custom receive adapter allows users to select and configure a WCF binding, behavior, and behavior extensions for the receive location running in an in-process host.

The WCF-CustomIsolated adapter enables the use of Windows Communication Foundation (WCF) extensibility features over the HTTP transport. The WCF-CustomIsolated adapter allows users to select and configure a WCF binding, behavior, and behavior extensions for the receive location running in an isolated host. To use the WCF-CustomIsolated adapter, you must create in Microsoft Internet Information Services (IIS) the virtual directory corresponding to this receive location by using the BizTalk WCF Service Publishing Wizard.

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
<td>Required. If you use the WCF-Custom receive adapter, specify the fully qualified URI of the service that this receive location publishes. The available transport scheme for this property is determined by the <strong>Binding Type</strong> property on the <strong>Binding</strong> tab. If you use the WCF-CustomIsolated adapter, specify the URI for this receive location. Specify the virtual directory plus the .svc file name that the BizTalk WCF Service Publishing Wizard generates—for example, /path/service.svc. <strong>Note:</strong> You can also import and export this property through the <strong>Import/Export</strong> tab.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 255<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Endpoint Identity</strong></td>
<td>Optional. Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the WCF infrastructure will ensure that the identity of the expected service matches the values of this element. The values that can be specified for the <strong>Endpoint Identity</strong> property differ according to the security configuration. <strong>Note:</strong> You can also import and export this property through the <strong>Import/Export</strong> tab. If the receive location is configured to use multiple identity types, only the identity type with the lowest number can be exported. For example, if <strong>1. DNS</strong> and <strong>4. RSA</strong> are both set in the <strong>Identity Editor</strong> dialog box, only the <strong>1. DNS</strong> property is saved by using the <strong>Export</strong> tab.<br />
<br />
The default value is an empty string.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-Custom Receive Location](https://msdn.microsoft.com/library/bb259941\(v=bts.80\))  
[How to Configure a WCF-CustomIsolated Receive Location](https://msdn.microsoft.com/library/bb226374\(v=bts.80\))  
[Publishing Service Metadata for the WCF Receive Adapters](https://msdn.microsoft.com/library/bb246083\(v=bts.80\))  
[Configuring IIS for the Isolated WCF Receive Adapters](https://msdn.microsoft.com/library/bb245982\(v=bts.80\))  
[Publishing WCF Services with the Isolated WCF Receive Adapters](https://msdn.microsoft.com/library/bb226318\(v=bts.80\))  
[The \<identity\> element](http://go.microsoft.com/fwlink/?linkid=75747)

