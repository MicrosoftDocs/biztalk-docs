---
title: "Use Performance Counters with the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performance counters, using"
  - "troubleshooting, using performance counters"
ms.assetid: 2749add3-31f1-47ff-b3b4-ef46c76fa533
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use Performance Counters with the SAP adapter
Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use performance counters to gauge the performance of the adapters. The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category "[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]" along installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
  
## LOB Time (Cumulative) Performance Counter  
 The **BizTalk .NET Adapter for SAP** category has one performance counter called the "LOB Time (Cumulative)". This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] creates an instance of the performance counter in the following pattern:  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 The endpoint ID could be:  
  
- For calls from the adapter to the SAP system (outbound)  
  
  -   A,\<application server host\>,\<system number\>  
  
  -   B,\<message server host\>,\<R3NAME\>  
  
  -   D,\<destination\>  
  
- For calls from the SAP system to the adapter (inbound)  
  
  -   I,\<gateway host\>,\<gateway server\>  
  
  -   ID,\<destination\>  
  
  The action ID could be:  
  
- \<RFC name\> (for an RFC call)  
  
- T,\<RFC name\> (for a tRFC call)  
  
  The performance counter is initialized only after the adapter makes the first call to the SAP system. Also, the [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx) property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates.
  
> [!NOTE]
>  The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.  
  
## Enabling Performance Counters  
 The performance counters can be enabled or disabled by setting the binding property *EnablePerformanceCounters*. To enable performance counters, set the *EnablePerformanceCounters* binding property to **True**. To disable performance counters, set *EnablePerformanceCounters* to **False**. By default, *EnablePerformanceCounters* is set to **False**.  
  
## Performance Counters and the WCF LOB Adapter SDK  
 Changing the value of the *EnablePerformanceCounters* binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic. Hence, if there are two instances of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding in the AppDomain, and the *EnablePerformanceCounters* binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other. However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.  
  
## See Also  

[Troubleshoot the SAP adapter](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)