---
description: "Learn more about: IOneWayAsyncTxn.BeginOneWayMethod Method"
title: IOneWayAsyncTxn.BeginOneWayMethod Method
TOCTitle: IOneWayAsyncTxn.BeginOneWayMethod Method
ms:assetid: 673efbb7-cada-494c-946a-fd9306f35ea4
ms:mtpsurl: https://msdn.microsoft.com/library/Bb743430(v=BTS.80)
ms:contentKeyID: 51528615
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IOneWayAsyncTxn.BeginOneWayMethod Method

 

Asynchronously processes messages incoming through the WCF-NetMsmq one-way transactional receive locations.


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

[IOneWayAsyncTxn.EndOneWayMethod Method](ionewayasynctxn-endonewaymethod-method.md)

