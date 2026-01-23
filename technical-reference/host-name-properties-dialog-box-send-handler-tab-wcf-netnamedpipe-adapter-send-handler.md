---
description: "Learn more about: <Host Name> Properties Dialog Box, Send Handler Tab (WCF-NetNamedPipe Adapter Send Handler)"
title: <Host Name> Properties Dialog Box, Send Handler Tab (WCF-NetNamedPipe Adapter Send Handler)
TOCTitle: <Host Name> Properties Dialog Box, Send Handler Tab (WCF-NetNamedPipe Adapter Send Handler)
ms:assetid: 0af57e28-4ec1-4ad8-9063-730132bda452
ms:mtpsurl: https://msdn.microsoft.com/library/Bb743300(v=BTS.80)
ms:contentKeyID: 51526110
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netnamedpipe.sendhandler.sendhandler
ms.topic: ui-reference
---

# \<Host Name\> Properties Dialog Box, Send Handler Tab (WCF-NetNamedPipe Adapter Send Handler)

 

Use the **Send handler** tab to configure the send handler for the WCF-NetNamedPipe adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Maximum connections</strong></td>
<td>Specify the maximum number of outbound connections for each endpoint that is cached in the connection pool. This limits the number of connections that are cached for each unique remote endpoint. You should set this value to be greater than the maximum number of connections that you expect to be cached for any unique remote endpoint. If the number of active outbound connections exceeds this maximum value, then the service may appear unresponsive to the WCF-NetNamedPipe send ports running under this send hander.<br />
<br />
The default is 10.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-NetNamedPipe Send Handler](https://msdn.microsoft.com/library/bb727682\(v=bts.80\))

