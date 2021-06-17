---
description: "Learn more about: WCF-WSHttp Transport Properties Dialog Box, Receive, General Tab"
title: WCF-WSHttp Transport Properties Dialog Box, Receive, General Tab
TOCTitle: WCF-WSHttp Transport Properties Dialog Box, Receive, General Tab
ms:assetid: 530dd7e7-a610-4171-a3b0-06b7dd194a8a
ms:mtpsurl: https://msdn.microsoft.com/library/Bb246103(v=BTS.80)
ms:contentKeyID: 51528071
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-wshttp.transport.receive.general
---

# WCF-WSHttp Transport Properties Dialog Box, Receive, General Tab

 

Use the **General** tab to configure the receive location for the WCF-WSHttp adapter.


> [!NOTE]
> <P>If you use <STRONG>Transport</STRONG> or <STRONG>TransportWithMessageCredential</STRONG> for the <STRONG>Security mode</STRONG>, you must set up Secure Sockets Layer (SSL) in Microsoft Internet Information Services (IIS).</P>



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
<td>Required. Specify the URI for this receive location. Specify the virtual directory plus the .svc file name that the BizTalk WCF Service Publishing Wizard generates—for example, /path/service.svc.<br />
<br />
Default value: /<br />
<br />
Minimum length: 1<br />
<br />
Maximum length: 255</td>
</tr>
<tr class="even">
<td><strong>Endpoint Identity</strong></td>
<td>Optional. Specify the identity of the service that this receive location provides by clicking the <strong>Edit</strong> button. The values that can be specified for the <strong>Endpoint Identity</strong> property differ according to the security configuration. These settings enable the client to authenticate this receive location. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br />
<br />
The default is an empty string.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767</td>
</tr>
</tbody>
</table>


## See Also

[The \<identity\> element](/dotnet/framework/configure-apps/file-schema/wcf/identity)
[How to Configure a WCF-WSHttp Receive Location](https://msdn.microsoft.com/library/bb226482\(v=bts.80\))
[Publishing WCF Services with the Isolated WCF Receive Adapters](https://msdn.microsoft.com/library/bb226318\(v=bts.80\))
[Configuring IIS for the Isolated WCF Receive Adapters](https://msdn.microsoft.com/library/bb245982\(v=bts.80\))