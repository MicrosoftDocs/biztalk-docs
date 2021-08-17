---
description: "Learn more about: ITwoWayAsyncVoid.BizTalkSubmit Method"
title: ITwoWayAsyncVoid.BizTalkSubmit Method
TOCTitle: ITwoWayAsyncVoid.BizTalkSubmit Method
ms:assetid: 74caefa5-dd41-44e9-aecd-2c14724c91b3
ms:mtpsurl: https://msdn.microsoft.com/library/Bb743485(v=BTS.80)
ms:contentKeyID: 51528970
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# ITwoWayAsyncVoid.BizTalkSubmit Method

 

Causes the runtime to create WSDL operations in the metadata. This method should never get invoked.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Method Declaration

```C#
[OperationContract(IsOneWay = false, Action = "BizTalkSubmit")]
Message BizTalkSubmit(Message message);
```

## Return Value

This method throws the **NotSupportedException** if called.

## See Also

[NotSupportedException Class](/dotnet/api/system.notsupportedexception)