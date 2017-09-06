---
title: "Use Performance Counters with the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performance counters, troubleshooting"
  - "troubleshooting, performance counters"
  - "performance counters, using"
ms.assetid: 7930e8f6-5099-4a9c-b38a-13c9902635a6
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use Performance Counters with the Siebel adapter
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use the performance counters to gauge the performance of the adapters. The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category "[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]" along with the Adapter Pack installation.  
  
## The LOB Time (Cumulative) Performance Counter  
 The **BizTalk .NET Adapter for Siebel** category has one performance counter called "LOB Time (Cumulative)". This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] creates an instance of the performance counter for each action, for a specific Siebel server name. The instances are created in the following pattern:  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 In case of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], the endpoint id is the name of the Siebel server, as specified in the connection URI. The action id could be any action performed by the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] such as Login, Logoff, Metadata, \<business component name>.\<operation>, \<business service name>.\<business service method>. If the preceding naming convention results in a name that exceeds 127 characters only the action ID is displayed in the following format:  
  
```  
:::<action id>  
```  
  
 If `:::<action id>` also exceeds 127 characters, it is trimmed down to 127 characters.  
  
 The performance counter is initialized only after the adapter makes the first call to the Siebel system. Also, the **InstanceLifetime** property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates. 
  
> [!NOTE]
>  The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.  
  
## Enabling Performance Counters  
 The performance counters can be enabled or disabled by setting the binding property **EnablePerformanceCounters**. Set **EnablePerformanceCounters** binding property to **True** to enable performance counters. To disable performance counters, set **EnablePerformanceCounters** to **False**. By default, **EnablePerformanceCounters** is set to **False**.  
  
## Performance Counters and the WCF LOB Adapter SDK  
 Changing the value of the **EnablePerformanceCounters** binding property changes the value of the corresponding performance counter for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic. Hence, if there are two instances of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding in the AppDomain, and the **EnablePerformanceCounters** binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other. However, because the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False**, depending on what value was specified last.  
  
## See Also  
[Troubleshoot the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)