---
description: "Learn more about: WCF-NetTcp Transport Properties Dialog Box, Receive, General Tab"
title: WCF-NetTcp Transport Properties Dialog Box, Receive, General Tab
TOCTitle: WCF-NetTcp Transport Properties Dialog Box, Receive, General Tab
ms:assetid: c43745ae-6b1b-43d5-8da0-34e2f8259e4f
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226515(v=BTS.80)
ms:contentKeyID: 51531029
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-nettcp.transport.receive.general
---

# WCF-NetTcp Transport Properties Dialog Box, Receive, General Tab

 

Use the **General** tab to configure the receive location for the WCF-NetTcp adapter.

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
<td>Required. Specify the fully qualified URI with the <strong>net.tcp</strong> scheme for this receive location.<br />
<br />
Minimum length: 1<br />
<br />
Maximum length: 255<br />
<br />
Default value: net.tcp://localhost/</td>
</tr>
<tr class="even">
<td><strong>Endpoint Identity</strong></td>
<td>Optional. Specify the identity of the service that this receive location provides by clicking the <strong>Edit</strong> button. The values that can be specified for the <strong>Endpoint Identity</strong> property differ according to the security configuration. These settings enable the client to authenticate this receive location. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br />
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

[The \<identity\> element](/dotnet/framework/configure-apps/file-schema/wcf/identity)
[How to Configure a WCF-NetTcp Receive Location](https://msdn.microsoft.com/library/bb226412\(v=bts.80\))
[Publishing Service Metadata for the WCF Receive Adapters](https://msdn.microsoft.com/library/bb246083\(v=bts.80\))