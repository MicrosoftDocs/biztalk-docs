---
title: IOneWayAsync.BeginOneWayMethod Method
TOCTitle: IOneWayAsync.BeginOneWayMethod Method
ms:assetid: 4a5baf9c-e601-4a52-9e01-7e8eff8a746d
ms:mtpsurl: https://msdn.microsoft.com/library/Bb727826(v=BTS.80)
ms:contentKeyID: 51527844
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IOneWayAsync.BeginOneWayMethod Method

 

Asynchronously processes messages incoming through the WCF-NetMsmq one-way non-transactional receive locations.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Method Declaration

```C#
[OperationContract(AsyncPattern = true, IsOneWay = true, Action = "*")]  
IAsyncResult BeginOneWayMethod(Message message, AsyncCallback callback, object state);  
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

[IOneWayAsync.EndOneWayMethod Method](ionewayasync-endonewaymethod-method.md)

