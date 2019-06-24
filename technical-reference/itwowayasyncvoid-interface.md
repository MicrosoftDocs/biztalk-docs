---
title: ITwoWayAsyncVoid Interface
TOCTitle: ITwoWayAsyncVoid Interface
ms:assetid: d453d7ec-d49c-401d-b21f-0ffb28220fd1
ms:mtpsurl: https://msdn.microsoft.com/library/Bb743686(v=BTS.80)
ms:contentKeyID: 51531482
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# ITwoWayAsyncVoid Interface

 

The **ITwoWayAsyncVoid** interface is used for the WCF one-way receive locations that do not support a transaction protocol, excluding the WCF-NetMsmq adapter. The WCF adapters asynchronously process messages incoming through this interface.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Interface Declaration

```C#
[ServiceContract(Namespace = http://www.microsoft.com/biztalk/2006/r2/wcf-adapter")]  
public interface ITwoWayAsyncVoid  
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
<td><a href="itwowayasyncvoid-begintwowaymethod-method.md">ITwoWayAsyncVoid.BeginTwoWayMethod Method</a></td>
<td>Asynchronously processes messages incoming through the WCF one-way receive locations that do not support a transaction protocol, excluding the WCF-NetMsmq adapter.</td>
</tr>
<tr class="even">
<td><a href="itwowayasyncvoid-endtwowaymethod-method.md">ITwoWayAsyncVoid.EndTwoWayMethod Method</a></td>
<td>&lt;End&gt; method corresponding to <strong>BeginTwoWayMethod</strong> for the asynchronous operation implementation.</td>
</tr>
<tr class="odd">
<td><a href="itwowayasyncvoid-biztalksubmit-method.md">ITwoWayAsyncVoid.BizTalkSubmit Method</a></td>
<td>Causes the runtime to create WSDL operations in the metadata. This method should never get invoked</td>
</tr>
</tbody>
</table>

