---
title: IOneWayAsyncTxn Interface
TOCTitle: IOneWayAsyncTxn Interface
ms:assetid: 9df99847-61a4-4975-be48-8bbb72c8f00a
ms:mtpsurl: https://msdn.microsoft.com/library/Bb743620(v=BTS.80)
ms:contentKeyID: 51529996
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IOneWayAsyncTxn Interface

 

The **IOneWayAsync** interface is used for the WCF-NetMsmq one-way transactional receive locations. The WCF adapters asynchronously process messages incoming through this interface.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Interface Declaration

```C#
[ServiceContract(Namespace = http://www.microsoft.com/biztalk/2006/r2/wcf-adapter")]  
public interface IOneWayAsyncTxn  
```

## Public Methods

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="ionewayasynctxn-beginonewaymethod-method.md">IOneWayAsyncTxn.BeginOneWayMethod Method</a></td>
<td>Asynchronously processes messages incoming through the WCF-NetMsmq one-way transactional receive locations.</td>
</tr>
<tr class="even">
<td><a href="ionewayasynctxn-endonewaymethod-method.md">IOneWayAsyncTxn.EndOneWayMethod Method</a></td>
<td>&lt;End&gt; method corresponding to <strong>BeginTwoWayMethod</strong> for the asynchronous operation implementation.</td>
</tr>
<tr class="odd">
<td><a href="ionewayasynctxn-biztalksubmit-method.md">IOneWayAsyncTxn.BizTalkSubmit Method</a></td>
<td>Causes the runtime to create WSDL operations in the metadata. This method should never get invoked.</td>
</tr>
</tbody>
</table>

