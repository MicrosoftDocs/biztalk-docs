---
title: "Testing BizTalk Server Virtualization Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d09121b1-cdd6-4c01-9d69-0f1923464f0e
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Testing BizTalk Server Virtualization Performance
Each of the performance test scenarios described in this guide were deployed on physical computers in a Microsoft test lab, and then the same load test was performed on each distinct system architecture. The host operating system on each physical computer was a full installation of [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] Enterprise, 64-Bit Edition, with the Hyper-V server role installed. The virtual machines used for testing BizTalk Server were set up with [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] Enterprise, 64-Bit Edition as the guest operating system. The virtual machine used for testing SQL Server was set up with [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] Enterprise, 64-Bit Edition as the guest operating system. The test scenarios, test methods, performance test results, and subsequent analysis were used to formulate a series of best practices and guidance for designing, implementing, and optimizing virtualized [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
- **Test Scenario 1: Baseline** – The first scenario was designed to establish baseline performance of a BizTalk Server environment running on physical hardware only. For this scenario both BizTalk Server and SQL Server were installed and run on physical hardware only.  
  
- **Test Scenario 2: Virtual BizTalk Server/Physical SQL Server** - The second scenario was designed to determine the performance impact of hosting BizTalk Server on multiple guest virtual machines on the same physical server. Test results taken from multiple virtual machine configurations were then compared to a physical machine processing with the same number of logical processors as the total number dispersed across all virtual machines.  
  
- **Test Scenario 3: Virtual BizTalk Server/Virtual SQL Server on separate physical Hyper-V hosts** - The third scenario was conducted to determine the performance impact of running both BizTalk Server and SQL Server in a virtualized environment. Tests were performed using BizTalk Server running on Hyper-V virtual machines with the BizTalk databases hosted on a SQL Server instance running on a Hyper-V virtual machine. For this scenario, the BizTalk Server virtual machines and the SQL Server virtual machines were hosted on separate physical Hyper-V hosts.  
  
- **Test Scenario 4: Server consolidation - Consolidating a full BizTalk Group Including SQL onto one Physical Server on Hyper-V** – In the scenario, all virtual machines (VMs) needed to run the test application are hosted on one physical server. The purpose of this scenario is to determine the performance costs of hosting SQL Server and BizTalk Server virtual machines in a consolidated environment.  
  
  This section provides an overview of the test application and the server architecture used for each scenario and also presents key performance indicators (KPIs) observed during testing.  
  
## In This Section  
  
-   [Test Scenario Overview](../technical-guides/test-scenario-overview.md)  
  
-   [Test Scenario Server Architecture](../technical-guides/test-scenario-server-architecture.md)  
  
-   [Test Results: BizTalk Server Key Performance Indicators](../technical-guides/test-results-biztalk-server-key-performance-indicators.md)  
  
-   [Test Results: SQL Server Key Performance Indicators](../technical-guides/test-results-sql-server-key-performance-indicators.md)  
  
-   [Test Results: Networking Key Performance Indicators](../technical-guides/test-results-networking-key-performance-indicators.md)  
  
-   [Test Results: Memory Key Performance Indicators](../technical-guides/test-results-memory-key-performance-indicators.md)  
  
-   [Summary of Test Results](../technical-guides/summary-of-test-results.md)