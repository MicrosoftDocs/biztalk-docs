---
description: "Learn more about: Adjusting Throttling Thresholds: When and Why"
title: "Adjusting Throttling Thresholds: When and Why"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Adjusting Throttling Thresholds: When and Why
When it comes to throttling, one size does not fit all. There are a range of factors that will determine what the optimal settings should be. Out of the box, BizTalk Server provides default values that have been proven through testing to effectively protect a system from things like backlog overages. However, for some scenarios, this may be too aggressive. The following examples illustrate this point.  
  
## Example 1: Peak Loads and Database Size  
 Each solution built on BizTalk Server has a maximum sustainable throughput (MST). As long as load stays below this level, the system can sustain that load indefinitely, by definition. In practice, however, it is more common to have peaks and valleys in the load profile than it is to have a steady load that doesn’t vary over time.  
  
 Rather than build a system that is capable of sustaining the highest peak loads indefinitely, it is more cost effective to build a system that can handle some backlog under peak load, and recover during the valleys. However, if the backlog expected during the peak loads is higher than the default throttling value for database size, then the system will block the backlog by throttling the input. If this is not desirable, for example, because you need all of the input files to be consumed as quickly as possible, then the solution is to raise the database size threshold to accept the expected backlog before throttling.  
  
## Example 2: Memory Usage Optimization  
 Another resource that throttling uses in order to gauge processing speed is how much memory is available to host processes. If the available memory gets too small compared to the threshold, throttling will slow down the number of messages the engine retrieves from the host queues to be worked on. Given the variability in the amount and availability of memory on today’s enterprise class servers, especially with x64 support in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the threshold may very well need to be raised or lowered to optimize memory usage.  
  
## Recommendation  
 Throttling in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is configured by default to provide good protection for the system out of the box. The default settings should not, however, be taken for granted as optimal. Monitor the performance counters for throttling states to see if throttling is taking place, then gauge for yourself if the resource on which throttling is based (for example, database size or memory usage) is under or over utilized, then adjust the throttling thresholds up or down accordingly.
