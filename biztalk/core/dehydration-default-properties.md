---
title: "Dehydration Default Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68c59def-d73b-4880-9884-ccbe5d982f4b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Dehydration Default Properties
Following are the names of the dehydration properties and their default values. These properties are configurable in [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] or as XML in the BizTalk configuration file (BTSNTSvc.exe.config or BTSNTSvc64.exe.config). The values in the BizTalk configuration file are applied first. Then, the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] settings are applied. The dehydration properties are read when all host instances containing an orchestration start.  
  
> [!IMPORTANT]
>  Not all orchestrations settings are exposed in [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]. For these settings, the BizTalk configuration file (BTSNTSvc.exe.config or BTSNTSvc64.exe.config) is used. When using the BizTalk configuration file, many properties are not listed. These properties and their default values are still applied, even if they are not explicitly specified in the configuration file.  
  
 To change the default values, you can use [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] or explicitly add them to the BizTalk configuration file. For more information, see [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) and [BTSNTSvc.exe.config File](../core/btsntsvc-exe-config-file.md).  
  
 **Dehydration**  
  
- **MaxThreshold** = 1800  
  
- **MinThreshold** = 1  
  
- **ConstantThreshold** = -1  
  
  **VirtualMemoryThrottlingCriteria**  
  
- **OptimalUsage** = 900  
  
- **MaximalUsage** =  1300  
  
- **IsActive** = true  
  
  **PrivateMemoryThrottlingCriteria**  
  
- **OptimalUsage** = 50  
  
- **MaximalUsage** =  350  
  
- **IsActive** = true  
  
  **PhysicalMemoryThrottlingCriteria**  
  
- **OptimalUsage** = 90  
  
- **MaximalUsage** =  95  
  
- **IsActive** = false  
  
  Each of these properties is described in detail next.  
  
## Dehydration  
 **MaxThreshold** and **MinThreshold** are the upper and lower bounds, in seconds, of the time that an orchestration can be blocked at a subscription (that is, blocked by a receive, listen, or delay) before being dehydrated. There will also be a value calculated at run-time, called **TestThreshold**, and its value, measured in seconds, is between **MinThreshold** and **MaxThreshold**.  
  
 If you set a value besides the default of -1 for **ConstantThreshold**, there will not be a run-time value **TestThreshold**. When an orchestration is blocked at a subscription, and the history of how long all instances of that orchestration have been blocked at that subscription is greater than the value of **TestThreshold**, then the orchestration will dehydrate. Otherwise, if the history is less than **TestThreshold** value the orchestration will not dehydrate. Also, even if the history indicates that dehydration will not take place, if the current blocking time reaches 2<em>**TestThreshold</em>*, then the dehydration will take place. The history is defined by the average of the last 10 waiting times in seconds, or the average of however many waiting times there are in the history if the waiting times are less than 10.  
  
 When the value of **TestThreshold** tends toward **MinThreshold** as memory usage increases, it is called "memory based dehydration throttling." Memory-based dehydration throttling allows more orchestration instances to be live because when any of them are blocked waiting for work (that is, waiting for a message or a delay), they can be dehydrated and taken out of memory. **TestThreshold** is a monotonically decreasing function of memory usage, it is inversely proportional to memory usage.  
  
 Following are descriptions of the individual Dehydration properties:  
  
-   **MaxThreshold**: the upper bounds, in seconds, of the time that an orchestration can be blocked at a subscription before being dehydrated.  
  
-   **MinThreshold**: the lower bounds, in seconds, of the time that an orchestration can be blocked at a subscription before being dehydrated.  
  
-   **ConstantThreshold**: the dynamic threshold, which usually fluctuates between the minimum and maximum values specified. However, you can make the threshold a fixed value by setting this property. A value of -1 tells the engine not to use a constant threshold. Don't set this property to a value other than -1 because it will disable dehydration based throttling.  
  
## VirtualMemoryThrottlingCriteria  
 Currently, virtual memory can become a bottleneck on 32-bit machines due to unmanaged heap fragmentation, so you should throttle by this resource as well. You should re-configure if /3GB is set or if the hosts are running on a 64-bit platform. Optimal and maximal usages are in MB.  
  
 Following are descriptions of the individual VirtualMemoryThrottlingCriteria properties:  
  
-   **OptimalUsage**: The amount of virtual memory usage at which dehydration throttling begins to take effect. At this point, **TestThreshold** has the value **MaxThreshold** and any memory usage greater than **OptimalUsage** causes **TestThreshold** to be less than **MaxThreshold**.  
  
-   **MaximalUsage**: The amount of virtual memory usage at which dehydration throttling is at a maximum. At this point, **TestThreshold** has the value **MinThreshold** and any memory usage less than **MaximalUsage** causes **TestThreshold** to be greater than **MinThreshold**.  
  
-   **IsActive**: A boolean value indicating if virtual memory throttling is active.  
  
## PrivateMemoryThrottlingCriteria  
 This property is a useful criterion for throttling, but appropriate values depend on whether the computer is running other windows services. If the computer has a lot of memory and is not being shared with other windows services, then you can increase these values significantly.  
  
 Following are descriptions of the individual PrivateMemoryThrottlingCriteria properties:  
  
-   **OptimalUsage**: the amount of private memory usage, in MB, at which dehydration throttling begins to take effect. At this point **TestThreshold** has the value **MaxThreshold** and any memory usage greater than **OptimalUsage** causes **TestThreshold** to be less than **MaxThreshold**.  
  
-   **MaximalUsage**: the amount of private memory usage, in MB, at which dehydration throttling is at a maximum. At this point **TestThreshold** has the value **MinThreshold** and any memory usage less than **MaximalUsage** causes **TestThreshold** to be greater than **MinThreshold**.  
  
-   **IsActive**: a boolean value indicating if private memory throttling is active.  
  
## PhysicalMemoryThrottlingCriteria  
 There is also a physical memory throttling where numbers are measured in percentage of memory used rather than MB. This property is disabled by default, but you can enable if needed.  
  
 Following are descriptions of the individual PhysicalMemoryThrottlingCriteria properties:  
  
-   **OptimalUsage**: the optimum percentage of physical memory to use for the host instances.  
  
-   **MaximalUsage**: the maximum percentage of physical memory to use for the host instances.  
  
-   **IsActive**: boolean value indicating if physical memory throttling is active.  
  
## Dehydration Properties Behavior  
 BizTalk Server uses these dehydration properties to decide when to dehydrate and rehydrate orchestrations. Under normal load, the default dehydration values are sufficient, but if you are running under heavy load and want to change performance characteristics, you should do the tuning yourself.  
  
 The dehydration behavior of BizTalk Server depends entirely on how much memory is available and how much memory is being used. The dehydration behavior is different with different amounts of memory and differences in memory use between 32-bit and 64-bit hosts.  
  
 The dehydration properties distinguish between Private Bytes and Virtual Bytes for the orchestration host:  
  
-   **Virtual Bytes**. This is thecurrent size, in bytes, of the virtual address space the process is using. Use of virtual address space does not necessarily imply corresponding use of either disk or main memory pages. Virtual space is finite, and the process can limit its ability to load libraries.  
  
-   **Private Bytes**. This is the current size, in bytes, of memory that this process has allocated that cannot be shared with other processes.