---
title: IOneWayAsyncTxn.BizTalkSubmit Method
TOCTitle: IOneWayAsyncTxn.BizTalkSubmit Method
ms:assetid: 2948d639-17ad-4797-bc0c-527db9bc7a01
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb727701(v=BTS.80)
ms:contentKeyID: 51526972
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IOneWayAsyncTxn.BizTalkSubmit Method

 

Causes the runtime to create WSDL operations in the metadata. This method should never get invoked.


> [!WARNING]
> <P>This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.</P>



## Method Declaration

``` 
[OperationContract(IsOneWay = true, Action = "BizTalkSubmit")]  
Message BizTalkSubmit(Message message);  
```

## Return Value

This method throws the **NotSupportedException** if called.

## See Also

[NotSupportedException Class](http://go.microsoft.com/fwlink/?linkid=88629)

