---
title: IOneWayAsync Interface
TOCTitle: IOneWayAsync Interface
ms:assetid: 2bea4f47-a49d-4398-bb9d-d48f3a3031bc
ms:mtpsurl: https://msdn.microsoft.com/library/Bb727707(v=BTS.80)
ms:contentKeyID: 51527049
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IOneWayAsync Interface

 

The **IOneWayAsync** interface is used for the WCF-NetMsmq one-way non-transactional receive locations. The WCF adapters asynchronously process messages incoming through this interface.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Interface Declaration

```C#
[ServiceContract(Namespace = http://www.microsoft.com/biztalk/2006/r2/wcf-adapter")]  
public interface IOneWayAsync  
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
<td><a href="ionewayasync-beginonewaymethod-method.md">IOneWayAsync.BeginOneWayMethod Method</a></td>
<td>Asynchronously processes messages incoming through the WCF-NetMsmq one-way non-transactional receive locations.</td>
</tr>
<tr class="even">
<td><a href="ionewayasync-endonewaymethod-method.md">IOneWayAsync.EndOneWayMethod Method</a></td>
<td>&lt;End&gt; method corresponding to <strong>BeginTwoWayMethod</strong> for the asynchronous operation implementation.</td>
</tr>
<tr class="odd">
<td><a href="ionewayasync-biztalksubmit-method.md">IOneWayAsync.BizTalkSubmit Method</a></td>
<td>Causes the runtime to create WSDL operations in the metadata. This method should never get invoked.</td>
</tr>
</tbody>
</table>

