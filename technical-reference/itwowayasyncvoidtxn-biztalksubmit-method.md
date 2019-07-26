---
title: ITwoWayAsyncVoidTxn.BizTalkSubmit Method
TOCTitle: ITwoWayAsyncVoidTxn.BizTalkSubmit Method
ms:assetid: 3be75cd9-a235-478a-922c-dfcc287dc6b1
ms:mtpsurl: https://msdn.microsoft.com/library/Bb727786(v=BTS.80)
ms:contentKeyID: 51527473
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# ITwoWayAsyncVoidTxn.BizTalkSubmit Method

 

Causes the runtime to create WSDL operations in the metadata. This method should never get invoked.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Method Declaration

```C#
[OperationContract(IsOneWay = false, Action = "BizTalkSubmit")]  
[TransactionFlow(TransactionFlowOption.Mandatory)]  
Message BizTalkSubmit(Message message);  
```

## Return Value

This method throws the **NotSupportedException** if called.

## See Also

[NotSupportedException Class](http://go.microsoft.com/fwlink/?linkid=88629)

