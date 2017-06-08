---
title: "ITwoWayAsync Interface | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49978f17-67b7-4d95-be55-8ffc558a4efa
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ITwoWayAsync Interface
The **ITwoWayAsync** interface is used for the WCF request-response receive locations. The WCF adapters asynchronously process messages incoming through this interface.  
  
> [!WARNING]
>  This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.  
  
## Interface Declaration  
  
```  
[ServiceContract(Namespace = http://www.microsoft.com/biztalk/2006/r2/wcf-adapter")]  
public interface ITwoWayAsync  
```  
  
## Public Methods  
  
|Method|Description|  
|------------|-----------------|  
|[ITwoWayAsync.BeginTwoWayMethod Method](../core/itwowayasync-begintwowaymethod-method.md)|Asynchronously processes messages incoming through the WCF request-response receive locations.|  
|[ITwoWayAsync.EndTwoWayMethod Method](../core/itwowayasync-endtwowaymethod-method.md)|\<End> method corresponding to **BeginTwoWayMethod** for the asynchronous operation implementation.|  
|[ITwoWayAsync.BizTalkSubmit Method](../core/itwowayasync-biztalksubmit-method.md)|Causes the runtime to create WSDL operations in the metadata. This method should never get invoked|