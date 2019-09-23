---
title: IOneWayAsync.BizTalkSubmit Method
TOCTitle: IOneWayAsync.BizTalkSubmit Method
ms:assetid: f0b0f828-20ea-462b-bc6a-51b086c620d8
ms:mtpsurl: https://msdn.microsoft.com/library/Bb743798(v=BTS.80)
ms:contentKeyID: 51533309
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IOneWayAsync.BizTalkSubmit Method

 

Causes the runtime to create WSDL operations in the metadata. This method should never get invoked.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Method Declaration

```C#
[OperationContract(IsOneWay = true, Action = "BizTalkSubmit")]
Message BizTalkSubmit(Message message);
```

## Return Value

This method throws the **NotSupportedException** if called.

## See Also

[NotSupportedException Class](https://go.microsoft.com/fwlink/?linkid=88629)

