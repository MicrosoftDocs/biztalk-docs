---
title: ITwoWayAsync Interface
TOCTitle: ITwoWayAsync Interface
ms:assetid: 49978f17-67b7-4d95-be55-8ffc558a4efa
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb727810(v=BTS.80)
ms:contentKeyID: 51527814
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# ITwoWayAsync Interface

 

The **ITwoWayAsync** interface is used for the WCF request-response receive locations. The WCF adapters asynchronously process messages incoming through this interface.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Interface Declaration

``` 
[ServiceContract(Namespace = http://www.microsoft.com/biztalk/2006/r2/wcf-adapter")]  
public interface ITwoWayAsync  
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
<td><a href="itwowayasync-begintwowaymethod-method.md">ITwoWayAsync.BeginTwoWayMethod Method</a></td>
<td>Asynchronously processes messages incoming through the WCF request-response receive locations.</td>
</tr>
<tr class="even">
<td><a href="itwowayasync-endtwowaymethod-method.md">ITwoWayAsync.EndTwoWayMethod Method</a></td>
<td>&lt;End&gt; method corresponding to <strong>BeginTwoWayMethod</strong> for the asynchronous operation implementation.</td>
</tr>
<tr class="odd">
<td><a href="itwowayasync-biztalksubmit-method.md">ITwoWayAsync.BizTalkSubmit Method</a></td>
<td>Causes the runtime to create WSDL operations in the metadata. This method should never get invoked</td>
</tr>
</tbody>
</table>

