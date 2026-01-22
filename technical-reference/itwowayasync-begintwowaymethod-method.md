---
description: "Learn more about: ITwoWayAsync.BeginTwoWayMethod Method"
title: ITwoWayAsync.BeginTwoWayMethod Method
TOCTitle: ITwoWayAsync.BeginTwoWayMethod Method
ms:assetid: 0d8358f5-caf2-4209-b787-e490fe53d05f
ms:mtpsurl: https://msdn.microsoft.com/library/Bb743316(v=BTS.80)
ms:contentKeyID: 51526207
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# ITwoWayAsync.BeginTwoWayMethod Method

 

Asynchronously processes messages incoming through the WCF request-response receive locations.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Method Declaration

```C#
[OperationContract(AsyncPattern = true, IsOneWay = false, Action = "*", ReplyAction = "*")]  
IAsyncResult BeginTwoWayMethod(Message message, AsyncCallback callback, object state);  
```

## Parameters

`message`  
Message object constraining the WCF request message.

`callback`  
Callback object indicating the method to be called when the corresponding asynchronous operation completes.

`state`  
User-defined object that qualifies or contains information about the asynchronous operation.

## Return Value

This method returns the status of the asynchronous operation.

## See Also

[ITwoWayAsync.EndTwoWayMethod Method](itwowayasync-endtwowaymethod-method.md)

