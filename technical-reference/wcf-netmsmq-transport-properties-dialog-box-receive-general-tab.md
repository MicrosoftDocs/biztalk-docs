---
description: "Learn more about: WCF-NetMsmq Transport Properties Dialog Box, Receive, General Tab"
title: WCF-NetMsmq Transport Properties Dialog Box, Receive, General Tab
TOCTitle: WCF-NetMsmq Transport Properties Dialog Box, Receive, General Tab
ms:assetid: 4059915a-9a01-4b64-8349-4c4864bcb5d6
ms:mtpsurl: https://msdn.microsoft.com/library/Bb246053(v=BTS.80)
ms:contentKeyID: 51527528
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netmsmq.transport.receive.general
---

# WCF-NetMsmq Transport Properties Dialog Box, Receive, General Tab

 

Use the **Address** tab to configure the receive location for the WCF-NetMsmq adapter.

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
<td>Required. Specify the fully qualified URI with the <strong>net.msmq</strong> scheme for this receive location. For example, net.msmq://localhost/private/queueName. In addition, a public or private queue corresponding to the queue name in this address must be created before enabling this receive location. <strong>Note:</strong> If you use a private queue for this receive location, you cannot receive from a remote client. <strong>Note:</strong> If the WCF-NetMsmq receive adapter is running on Windows Vista, you can use subqueues included in Message Queuing (MSMQ) 4.0. Subqueues can be addressed as: net.msmq<em>://&lt;computer-name&gt;</em>/applicationQueue;subqueueName, where <em>computer name</em> is the name of the computer on which the queue resides and the applicationQueue is the name of the application-specific queue. For more information about subqueues included in MSMQ 4.0, see related topic in See Also section of this topic.<br />
<br />
Minimum length: 1<br />
<br />
Maximum length: 255<br />
<br />
Default value: net.msmq://localhost/</td>
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

[Subqueues](/previous-versions/windows/desktop/legacy/ms711414(v=vs.85))
[Public and private queues](/previous-versions/windows/it-pro/windows-server-2003/cc776346(v=ws.10))
[How to Configure a WCF-NetMsmq Receive Location](https://msdn.microsoft.com/library/bb259976\(v=bts.80\))
[Publishing Service Metadata for the WCF Receive Adapters](https://msdn.microsoft.com/library/bb246083\(v=bts.80\))