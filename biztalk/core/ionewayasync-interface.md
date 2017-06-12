---
title: "IOneWayAsync Interface | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2bea4f47-a49d-4398-bb9d-d48f3a3031bc
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IOneWayAsync Interface
The **IOneWayAsync** interface is used for the WCF-NetMsmq one-way non-transactional receive locations. The WCF adapters asynchronously process messages incoming through this interface.  
  
> [!WARNING]
>  This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.  
  
## Interface Declaration  
  
```  
[ServiceContract(Namespace = http://www.microsoft.com/biztalk/2006/r2/wcf-adapter")]  
public interface IOneWayAsync  
```  
  
## Public Methods  
  
|Method|Description|  
|------------|-----------------|  
|[IOneWayAsync.BeginOneWayMethod Method](../core/ionewayasync-beginonewaymethod-method.md)|Asynchronously processes messages incoming through the WCF-NetMsmq one-way non-transactional receive locations.|  
|[IOneWayAsync.EndOneWayMethod Method](../core/ionewayasync-endonewaymethod-method.md)|\<End> method corresponding to **BeginTwoWayMethod** for the asynchronous operation implementation.|  
|[IOneWayAsync.BizTalkSubmit Method](../core/ionewayasync-biztalksubmit-method.md)|Causes the runtime to create WSDL operations in the metadata. This method should never get invoked.|