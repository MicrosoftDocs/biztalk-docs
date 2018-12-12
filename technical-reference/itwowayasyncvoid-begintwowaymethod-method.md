---
title: ITwoWayAsyncVoid.BeginTwoWayMethod Method
TOCTitle: ITwoWayAsyncVoid.BeginTwoWayMethod Method
ms:assetid: 3f5f4351-9e16-4b14-98df-53edb9aa89e3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb727793(v=BTS.80)
ms:contentKeyID: 51527508
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# ITwoWayAsyncVoid.BeginTwoWayMethod Method

 

Asynchronously processes messages incoming through the WCF one-way receive locations that do not support a transaction protocol, excluding the WCF-NetMsmq adapter.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Method Declaration

```C#
[OperationContract(AsyncPattern = true, IsOneWay = false, Action = "*", ReplyAction = "*")]  
IAsyncResult BeginTwoWayMethod(Message message, AsyncCallback callback, object state);  
```

## Parameters

`message`  
Message object constraining the WCF request message

`callback`  
Callback object indicating the method to be called when the corresponding asynchronous operation completes.

`state`  
User-defined object that qualifies or contains information about the asynchronous operation.

## Return Value

This method returns the status of the asynchronous operation.

## See Also

[ITwoWayAsyncVoid.EndTwoWayMethod Method](itwowayasyncvoid-endtwowaymethod-method.md)

