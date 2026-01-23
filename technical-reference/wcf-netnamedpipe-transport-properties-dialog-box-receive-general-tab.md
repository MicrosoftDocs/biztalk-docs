---
description: "Learn more about: WCF-NetNamedPipe Transport Properties Dialog Box, Receive, General Tab"
title: WCF-NetNamedPipe Transport Properties Dialog Box, Receive, General Tab
TOCTitle: WCF-NetNamedPipe Transport Properties Dialog Box, Receive, General Tab
ms:assetid: 881b1fd1-6337-4026-baab-1de61594b95f
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226390(v=BTS.80)
ms:contentKeyID: 51529478
ms.date: 08/30/2017
ms.topic: ui-reference
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netnamedpipe.transport.receive.general
---

# WCF-NetNamedPipe Transport Properties Dialog Box, Receive, General Tab

 

Use the **General** tab to configure the receive location for the WCF-NetNamedPipe adapter. The WCF-NetNamedPipe adapter provides efficient cross-process communication in a .NET-to-.NET environment. The adapter uses the named pipe transport and messages have a binary encoding. This adapter cannot be used in cross-computer communication.

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
<td>Required. Specify the fully qualified URI with the <strong>net.pipe</strong> scheme for this receive location. For example, net.pipe://localhost/pipeName. <strong>Note:</strong> The WCF-NetNamedPipe receive adapter does not use the computer name part in the URI to decide the pipe name.<br />
<br />
Minimum length: 1<br />
<br />
Maximum length: 255<br />
<br />
Default value: net.pipe://localhost/</td>
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

[How to Configure a WCF-NetNamedPipe Receive Location](https://msdn.microsoft.com/library/bb259943\(v=bts.80\))
[The \<identity\> element](/dotnet/framework/configure-apps/file-schema/wcf/identity)
[Publishing Service Metadata for the WCF Receive Adapters](https://msdn.microsoft.com/library/bb246083\(v=bts.80\))