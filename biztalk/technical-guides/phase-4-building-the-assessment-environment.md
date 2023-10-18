---
description: "Learn more about: Phase 4: Building the Assessment Environment"
title: "Phase 4: Building the Assessment Environment"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Phase 4: Building the Assessment Environment
The Build lab phase of a performance assessment is used to install the hardware and software for the environment in conformance to the design decisions made in previous phases. Because the Build lab phase can be time consuming, it is not unusual for this phase to overlap earlier phases. In many scenarios, the hardware and operating system may be installed before a final decision has been made as to the application architecture. The Build lab phase of a performance assessment typically includes the tasks discussed in this topic.  
  
## Obtain all build-lab infrastructure at least a week in advance of the lab start date  
 Plan to have available all of the required hardware and software at least a week before the lab start date. This will ensure that valuable lab time is not wasted for want of the required infrastructure.  
  
## Configure third-party software systems  
 There may be third-party systems that need to be built out and configured before the lab can begin. If subject matter experts (SMEs) are required for these systems, be sure they are scheduled during the build-out and lab execution stages. Ensure that they thoroughly document their build-out procedures.  
  
## Install and configure the BizTalk Server environment  
 Detailed instructions for installing BizTalk Server and the required dependency software are in the [Installation and Upgrade Guides](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md). After successfully installing and configuring the BizTalk Server environment, complete the following tasks:  
  
-   Follow the recommendations listed in the [Operational Readiness Checklists](operational-readiness-checklists.md)
  
-   Follow the recommendations in [Optimizing Performance](../technical-guides/optimizing-performance.md).  
  
-   Ensure all computer times are properly synchronized.  
  
-   Verify MSDTC functionality between all computers in the environment.  
  
-   Ensure any custom tracing/logging is disabled unless absolutely needed.  
  
-   Install the Visual Studio Ultimate edition for load testing.  For more information about how to perform automated testing using Visual Studio, see [Using Visual Studio to Facilitate Automated Testing](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md).  
  
-   Setup Performance Monitor counters and logs, as needed.  
  
-   Setup a debugging computer to debug the solution if code changes are within the scope of the performance assessment.  
  
-   Defragment all hard drives.  
  
-   Disable antivirus real time scanning.  
  
-   Back up the Enterprise Single Sign-On Master Secret.  
  
## Install the BizTalk Server application to be tested  
 Installation of the application to be tested will typically include the following steps:  
  
1.  Use the BizTalk Server Administration console to do the following:  
  
    -   Create Hosts  
  
    -   Create Send/Receive Handlers.  
  
    -   Create Host instances.  
  
    -   Create BizTalk Server Applications.  
  
2.  Application installation:  
  
    1.  Deploy BizTalk Server binaries to the BizTalk Server group.  
  
    2.  Import bindings to the BizTalk Server group.  
  
    3.  GAC BizTalk Server and non-BizTalk Server binaries on all boxes.  
  
    4.  Ensure dependency components exist on all boxes.  
  
3.  Install dependency applications.  
  
4.  Configure transports and physical endpoints in the BizTalk Server Administration console.  
  
5.  Start services.  
  
6.  Perform basic smoke tests – Smoke tests are end-to-end functional tests that test the basic functionality of your solution.  
  
## Implement automated build and load testing  
 Implementation of an automated build and load testing process is arguably the cornerstone of a BizTalk Server performance assessment. An automated build process should be implemented if code changes are within the scope of the performance assessment. Automated load testing should be implemented for all load testing scenarios. The initial time investment required to implement automated build and load testing is quickly recouped, automation accommodates rapid and precise repetition of mundane build/testing tasks that are subject to human error. For more information about implementing an automated build and testing process, see [Implementing Automated Testing](../technical-guides/implementing-automated-testing.md) in this guide.  
  
## Configure performance monitoring  
 Accurate performance monitoring is critical to the success of the performance assessment. Determine which performance metrics should be evaluated based on the throughput and latency goals that were defined in the Scope phase. Performance monitoring should be performed on each computer in the BizTalk Server environment. See [Performance Counters](../core/performance-counters.md). Use the Performance Analysis of Logs tool (PAL) to generate HTML reports that graphically chart important performance counters and generate alerts when thresholds for these counters are exceeded. S [Performance Analysis of Logs (PAL) tool](https://github.com/clinthuffman/PAL).  
  
## Establish and document the solution’s baseline performance  
 Baseline performance should be calculated so that the effect of performance optimizations applied during the performance assessment can be measured.  
  
## See Also  
 [Phases of a Performance Assessment](../technical-guides/phases-of-a-performance-assessment.md)
