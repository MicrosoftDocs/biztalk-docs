---
title: "Summary of Test Results | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d95fbaa6-0e07-4086-bea2-0577d39ae7cd
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Summary of Test Results
This topic summarizes the results from the test scenarios.  
  
## Summary of Test Results  
 The [Testing BizTalk Server Virtualization Performance](../technical-guides/testing-biztalk-server-virtualization-performance.md) section of this guide describes the test application used and the configuration of the various [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environments against which the test application was run. The testing was performed to compare the performance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] / [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] environment running on physical hardware to the performance of the environment running on Hyper-V virtual machines. Key Performance Indicators (KPIs) measured during testing included the following;  
  
1. Message throughput measured on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers.  
  
2. Request-response latency measured on the Visual Studio Test client which submitted synchronous requests to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
3. Processor utilization and Batch requests per second observed on [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
4. Network throughput observed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers.  
  
5. Available memory for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers.  
  
### Throughput Comparison Sample Results  
 With all other factors being equal, throughput of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution as measured by the "BizTalk:Messaging/Documents processed/Sec" performance monitor counter ranged from 67% to 94.3% of the throughput attainable when both the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers and the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers in the environment were installed on physical hardware.  
  
 When the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers in the environment were installed on Hyper-V virtual machines, throughput of the solution was observed to decline significantly, this reduction in throughput can be attributed to the CPU overhead required by Hyper-V.  
  
### Latency Comparison Sample Results  
 With all other factors being equal, when the BizTalk Server computers used in the BizTalk Server environment were run on Hyper-V virtual machines, latency of the BizTalk Server solution as measured by the "BizTalk:Messaging Latency/Request-Response Latency (sec)" performance monitor counter ranged from 66.9% to 94.3% of the latency attainable when the BizTalk Server computers used in the BizTalk Server environment were installed on physical hardware.  
  
 When the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers in the environment were installed on Hyper-V virtual machines, throughput of the solution was observed to decline significantly, this reduction in throughput can be attributed to the CPU overhead required by Hyper-V on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] virtual machines.  
  
### SQL Server Processor Utilization and Batch Requests per Second Sample Results  
 SQL Server processor utilization as measured by \SQL\Processor(_Total)\\% Processor Time counter was approximately the same on all test environments, ranging from a low of 88% to a high of 90.1%. There is however a significant difference between the \SQL Server:SQL Statistics\Batch Requests/sec measured on the consolidated environment (4520) and the \SQL Server:SQL Statistics\Batch Requests/sec measured on the physical environment (6350). The \SQL Server:SQL Statistics\Batch Requests/sec performance monitor counter provides a good indicator of how much work is being performed by SQL Server. The reduction in Batch Requests/sec when SQL Server is running in a Hyper-V environment can be attributed to the CPU overhead required by Hyper-V.  
  
### BizTalk Server and SQL Server Network Throughput Sample Results  
 Network throughput for BizTalk Server running on Hyper-V virtual machines was observed to range from approximately 70% to 96% of the network throughput achieved on the physical BizTalk Servers, depending on the particular test environment. Network throughput for SQL Server running on a Hyper-V virtual machine was observed to range from approximately 68% to 81% of the network throughput achieved on the physical SQL Server, again depending on the particular test environment. The delta in the observed network throughput can be attributed to the resource requirements of the Hyper-V Hypervisor.  
  
### BizTalk Server and SQL Server Available Memory Sample Results  
 Total memory available to SQL Server and BizTalk Server as measured by the \Memory\Available Mbytes performance monitor counter was fairly consistent across all test scenarios.