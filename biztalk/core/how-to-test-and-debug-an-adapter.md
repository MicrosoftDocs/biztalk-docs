---
title: "How to Test and Debug an Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf6563ea-b4ea-4617-b3da-d31250d002ab
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Test and Debug an Adapter
Debugging run-time problems often requires a multifaceted approach. Data must be gathered from multiple sources such as software tracing, performance counters, event log entries, Windows Management Instrumentation (WMI) events, and debugging source code to determine the cause of problems or software bugs.  
  
 Because receive and send adapters run in the address space of the BizTalk service the debugger needs to be attached to the BtsNtSvc.exe process to debug an adapter. However for isolated receive adapters, the debugger needs to be attached to the process that hosts the adapter.  
  
 The adapter run-time code should be instrumented with tracing code to capture run-time diagnostics for troubleshooting. You can do this by using the Microsoft Enterprise Instrumentation Framework (EIF). Typically it is useful to add trace statements for different levels of severity, for example, tracing for error conditions only, tracing for errors and warnings, and finally tracing for errors, warnings, and informational statements. Further, more complex adapters may have separate subsystems that need to be traced in isolation from each other. For example, an adapter may have a network subsubsystem and a core subsystem; enabling tracing for all subsystems may generate an excessive amount of "noise" in some scenarios.  
  
 Performance counters should be added to capture rates and values at run time to give more information about the run-time behavior of the adapter. For example, an adapter might publish performance counters for the raw numbers of messages sent on a per-endpoint basis as well as the rate of messages sent per second.  
  
 WMI events may also be useful for some critical error scenarios.  For instance if an adapter hits a critical error that causes it to shut down a receive location, firing a WMI event allows an administrator to listen on that event and take appropriate action.  
  
## Adapter Testing  
 When you develop a custom adapter for BizTalk Server, remember that it should be developed to enterprise software quality. This means that you need to test the adapter thoroughly before shipping it. While it does not completely detail how adapters should be tested, this section gives an idea of what needs to be done. In general the testing of run-time code such as adapters should cover three broad categories: functional testing, stress testing, and performance testing.  
  
### Function Testing  
 The adapter should be tested for all permutations of its functionality, including both positive tests and negative tests. Positive tests should include but not be limited to the following scenarios:  
  
- Receive a message(s)  
  
- Transmit a message(s)  
  
- Transmit a message using a dynamic port  
  
- Disable receive locations  
  
- Update configuration  
  
- Ensure service windows are working for both receive and send adapters  
  
- Ensure transactional integrity for transacted adapters  
  
  Negative tests should include but not be limited to:  
  
- Receive a bad message(s)  
  
- Receive a mixed batch of messages, some good and some bad  
  
- Transmit failure  
  
- Retry successful  
  
- Retry fails, move to next transport successful  
  
- Move to next transport fails, suspend message  
  
- Transmit a mixed batch of messages  
  
- Database failover  
  
### Stress Testing  
 Adapters are run-time components and as such should meet the stringent requirements for run-time software. Typically stress testing is carried out by running scenarios under load for a period of time. Further high-stress and low-stress mean time between failure tests should be performed, whereby the adapter is run under load for a measured time period.  
  
 Some rough guidelines for these tests might be running the adapter at high stress for around 72 hours, where the number of messages through the adapter causes the CPU utilization to be around of 80 to 90 percent. For low stress, the CPU utilization would be around 30 to 40 percent for around 120 hours.  
  
### Performance Testing  
 Adapters should be developed with performance in mind. Before releasing an adapter you should validate its performance. It is important to ensure that its performance scales up and scales out; that is, adding more CPUs leads to a performance increase as does adding more computers. Profiling the code can help to eliminate performance bottlenecks.