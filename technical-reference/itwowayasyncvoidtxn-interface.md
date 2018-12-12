---
title: ITwoWayAsyncVoidTxn Interface
TOCTitle: ITwoWayAsyncVoidTxn Interface
ms:assetid: 8cd8f671-c322-4623-bd11-35f7b34b29e6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb743549(v=BTS.80)
ms:contentKeyID: 51529587
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# ITwoWayAsyncVoidTxn Interface

 

The **ITwoWayAsyncVoidTxn** interface is used for the WCF one-way receive locations that support a transaction protocol, excluding the WCF-NetMsmq adapter. The WCF adapters asynchronously process messages incoming through this interface.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Interface Declaration

```C#
[ServiceContract(Namespace = http://www.microsoft.com/biztalk/2006/r2/wcf-adapter")]  
public interface ITwoWayAsyncVoidTxn  
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
<td><a href="itwowayasyncvoidtxn-begintwowaymethod-method.md">ITwoWayAsyncVoidTxn.BeginTwoWayMethod Method</a></td>
<td>Asynchronously processes messages incoming through the WCF one-way receive locations that support a transaction protocol, excluding the WCF-NetMsmq adapter.</td>
</tr>
<tr class="even">
<td><a href="itwowayasyncvoidtxn-endtwowaymethod-method.md">ITwoWayAsyncVoidTxn.EndTwoWayMethod Method</a></td>
<td>&lt;End&gt; method corresponding to <strong>BeginTwoWayMethod</strong> for the asynchronous operation implementation.</td>
</tr>
<tr class="odd">
<td><a href="itwowayasyncvoidtxn-biztalksubmit-method.md">ITwoWayAsyncVoidTxn.BizTalkSubmit Method</a></td>
<td>Causes the runtime to create WSDL operations in the metadata. This method should never get invoked.</td>
</tr>
</tbody>
</table>

