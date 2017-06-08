---
title: "ITwoWayAsyncVoidTxn Interface | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cd8f671-c322-4623-bd11-35f7b34b29e6
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ITwoWayAsyncVoidTxn Interface
The **ITwoWayAsyncVoidTxn** interface is used for the WCF one-way receive locations that support a transaction protocol, excluding the WCF-NetMsmq adapter. The WCF adapters asynchronously process messages incoming through this interface.  
  
> [!WARNING]
>  This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.  
  
## Interface Declaration  
  
```  
[ServiceContract(Namespace = http://www.microsoft.com/biztalk/2006/r2/wcf-adapter")]  
public interface ITwoWayAsyncVoidTxn  
```  
  
## Public Methods  
  
|Method|Description|  
|------------|-----------------|  
|[ITwoWayAsyncVoidTxn.BeginTwoWayMethod Method](../core/itwowayasyncvoidtxn-begintwowaymethod-method.md)|Asynchronously processes messages incoming through the WCF one-way receive locations that support a transaction protocol, excluding the WCF-NetMsmq adapter.|  
|[ITwoWayAsyncVoidTxn.EndTwoWayMethod Method](../core/itwowayasyncvoidtxn-endtwowaymethod-method.md)|\<End> method corresponding to **BeginTwoWayMethod** for the asynchronous operation implementation.|  
|[ITwoWayAsyncVoidTxn.BizTalkSubmit Method](../core/itwowayasyncvoidtxn-biztalksubmit-method.md)|Causes the runtime to create WSDL operations in the metadata. This method should never get invoked.|