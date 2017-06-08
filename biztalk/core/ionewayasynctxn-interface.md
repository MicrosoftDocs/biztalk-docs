---
title: "IOneWayAsyncTxn Interface | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9df99847-61a4-4975-be48-8bbb72c8f00a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IOneWayAsyncTxn Interface
The **IOneWayAsync** interface is used for the WCF-NetMsmq one-way transactional receive locations. The WCF adapters asynchronously process messages incoming through this interface.  
  
> [!WARNING]
>  This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.  
  
## Interface Declaration  
  
```  
[ServiceContract(Namespace = http://www.microsoft.com/biztalk/2006/r2/wcf-adapter")]  
public interface IOneWayAsyncTxn  
```  
  
## Public Methods  
  
|Method|Description|  
|------------|-----------------|  
|[IOneWayAsyncTxn.BeginOneWayMethod Method](../core/ionewayasynctxn-beginonewaymethod-method.md)|Asynchronously processes messages incoming through the WCF-NetMsmq one-way transactional receive locations.|  
|[IOneWayAsyncTxn.EndOneWayMethod Method](../core/ionewayasynctxn-endonewaymethod-method.md)|\<End> method corresponding to **BeginTwoWayMethod** for the asynchronous operation implementation.|  
|[IOneWayAsyncTxn.BizTalkSubmit Method](../core/ionewayasynctxn-biztalksubmit-method.md)|Causes the runtime to create WSDL operations in the metadata. This method should never get invoked.|