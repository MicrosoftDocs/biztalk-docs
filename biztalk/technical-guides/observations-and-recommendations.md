---
title: "Observations and Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88289080-1a59-4ffc-a0b2-312ec21940c2
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Observations and Recommendations
## Test Results Summary  
 The results for the Messaging-only scenario were observed to be ~ 109,382,400 messages per day. For the Orchestration scenario, the results indicate that a single computer running BizTalk Server can process up to 58,752,000 messages per day. These results were achieved in a sandboxed environment using normal enterprise-class hardware deployed for many BizTalk Server solutions. Therefore, these results indicate the type of BizTalk Server performance of that can be achieved with no custom code. Customer solutions often involve custom-developed BizTalk artifacts; in many cases this increases processing requirements which in turn affects performance. By following the advice presented in this guide, particularly the [Optimizing BizTalk Server Applications](../technical-guides/optimizing-biztalk-server-applications.md) section, the impact of implementing custom-developed BizTalk Server artifacts can be minimized.  
  
 The following table provides a summary of the test results for this performance assessment.  
  
|Scenario|Messaging (BizTalk KPI – Documents Processed per Second)|Messaging (SQL KPI – SQL Processor Utilization)|Messaging Latency (Seconds)|Orchestration (BizTalk KPI – Documents Processed per Second)|Orchestration (SQL KPI – SQL Processor Utilization)|Orchestration Latency (Seconds)|  
|--------------|----------------------------------------------------------------|-------------------------------------------------------|-----------------------------------|--------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------------|  
|Single MessageBox 1 BizTalk Server computer|1266 documents processed per second|59% SQL CPU utilization|0.06|680 documents processed per second|66.5% SQL CPU utilization|0.067|  
|Single MessageBox 2 BizTalk Server computers|1267 documents processed per second|59.8% SQL CPU utilization|0.057|686 documents processed per second|68.5% SQL CPU utilization|0.067|  
|3 MessageBox 1 BizTalk Server computers|2102 documents processed per second|41% SQL CPU utilization|0.077|974 documents processed per second|48% SQL CPU utilization|0.11|  
|3 MessageBox 2 BizTalk Server computers|2285 documents processed per second|58% SQL CPU utilization|0.041|1065 documents processed per second|65% SQL CPU utilization|0..69|  
|4 MessageBoxes 1 BizTalk Server computers|2125 documents processed per second|30% SQL CPU utilization|0.078|979 documents processed per second|37% SQL CPU utilization|0.095|  
|4 MessageBoxes 2 BizTalk Server computers|2790 documents processed per second|50% SQL CPU utilization|0.052|1487 documents processed per second|63% SQL CPU utilization|0.15|  
|4 MessageBoxes 3 BizTalk Server computers|2656 documents processed per second|58% SQL CPU utilization|0.074|1388 documents processed per second|65% SQL CPU utilization|0.15|  
  
## Comparison of performance statistics with BizTalk Server 2009  
 The following table shows a comparison of performance statistics between BizTalk Server 2009 and BizTalk Server 2010. The BizTalk Server 2009 performance statistics listed in this table are from the BizTalk Server 2009 Performance and Optimization Guide.  
  
|Scenario|BizTalk Server 2009<br /> Maximum Sustainable Throughput (MST) msgs/sec|BizTalk Server 2009<br />Number of BizTalk Servers needed|BizTalk Server 2010<br />Maximum Sustainable Throughput (MST) msgs/sec|BizTalk Server 2010<br />Number of BizTalk Servers needed|BizTalk Server 2010 % difference from BizTalk Server 2009|  
|--------------|----------------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------------------------------------|  
|Messaging - Single MessageBox|1291|2|1266|1|98.06%|  
|Orchestration - Single MessageBox|676|2|680|1|100.59%|  
|Messaging - 3 MessageBoxes|2103|3|2285|2 (2102/sec with 1 BTS)|108.65%|  
|Messaging - 4 MessageBoxes|Not applicable|Not applicable|2790|2|Not applicable|  
|Orchestration - 3 MessageBoxes|1005|4|1065|2 (974/sec with 1 BTS)|105.97%|  
|Orchestration - 4 MessageBoxes|Not applicable|Not applicable|1487|2|Not applicable|  
  
 In our lab environment, when using four MessageBox databases, the maximum sustainable throughput results were as follows:  
  
- For messaging scenario, 2790 documents per second.  
  
- For orchestration scenario, 1487 documents per second.  
  
  **Message considerations** While BizTalk Server imposes no restriction on message size, the tests we ran for BizTalk Server 2010 used 2-KB messages only and the type of WCF adapter used was WCF-NetTCP adapter. This matches the message size and adapter type used in the testing for the BizTalk Server 2009 Performance Optimization Guide.  
  
  The drivers for the performance improvement are:  
  
1.  **Hardware advancements** - The SQL Server computers used in our lab were 4-CPU, quad-core (16 cores), Intel Xeon E7330 @ 2.40 GHz. In the 2009 tests, 4-CPU, quad-core (16 cores), Intel Xeon 2.4 GHz were used.  
  
     The BizTalk Server computers used in our lab were 2-CPU, quad-core (8 cores), Nehalem Hyper-Threaded (16 logical cores), Intel Xeon X5570 @ 2.93 GHz. In the 2009 tests, 2-CPU, quad-core (8 cores), Intel Xeon 2.33 GHz were used.  
  
2.  **Improvement of SQL Server Engine** - The tests in 2009 were performed against SQL Server 2008, whereas our tests were performed with SQL Server 2008 R2 as the underlying database platform.  
  
## Recommendations for scaling the BizTalk Server and SQL Server tiers  
 With these results, the BizTalk Server Product Team was able to demonstrate that a single BizTalk Server computer and a single SQL Server computer can support over 109 million messages in a messaging scenario and 58 million orchestrations during a 24-hour period. By scaling the BizTalk Server and SQL tiers to the optimal configuration available in our environment, we were able to process over241 million messages per day and over 128 million orchestrations. The results were performed in a sandboxed environment by using the class of hardware deployed in many enterprises. As stated earlier, these numbers represent realistic performance of BizTalk Server that can be achieved with no custom code and an optimized environment.  With additional hardware, it is possible that even greater performance could have been achieved. Customer solutions often involve custom-developed BizTalk artifacts that incur additional processing requirements, hence increasing resource utilization and in turn reducing overall performance. However, by following the advice outlined throughout the guide, particularly the recommendations in [Optimizing BizTalk Server Applications](../technical-guides/optimizing-biztalk-server-applications.md), the impact of this can be minimized.  
  
 The results demonstrate that scaling out the number of BizTalk Server computers is an effective scale-out strategy if the MessageBox SQL Server computer is not a bottleneck. After a certain point our results indicate that adding BizTalk Server computers becomes an ineffective scale-out technique because we observed that a contention point occurred on the shared tables within the MessageBox database, which caused performance to diminish. To maximize the results that can be obtained from a BizTalk Server group with a single MessageBox database, you should apply the optimizations described in [Optimizing Database Performance](../technical-guides/optimizing-database-performance.md). In particular, you should ensure that a fast storage subsystem is used for the SQL Server storage and that the logical disks used by SQL Server to store the MessageBox database files respond in the shortest possible time. A commonly used threshold for measuring acceptable read/write performance is 15 milliseconds; typically this is measured by the Avg. Disk sec/Read and Avg. Disk sec/Write counters that can be found under the Logical Disk performance object. Once all available optimizations have been applied to the SQL Server computer that hosts the MessageBox database, additional MessageBox databases can be added. The same optimization techniques that were applied to the primary MessageBox database should also be applied to the secondary databases. We recommend that you follow the guidelines in [Scaling Out the SQL Server Tier](http://go.microsoft.com/fwlink/?LinkID=158075) (http://go.microsoft.com/fwlink/?LinkID=158075) in the BizTalk Server documentation.  
  
 To gain optimal results, the whole hardware and software stack needs to be of appropriate quality and also configured correctly. First, good quality hardware should be purchased including, but not limited to, gigabit networking, fast storage (SAN or 15-K local SQL disks) and modern computers that have multiple CPUs with multiple cores per CPU. The SQL Server computer should be dedicated to BizTalk Server processing only. When running a single SQL Server computer, we recommend that two instances of SQL be created, one for the BizTalk MessageBox and one for all other databases. This enables instance-wide settings to be configured for optimal performance of the MessageBox. The optimizations recommended in [Optimizing Performance](../technical-guides/optimizing-performance.md) should be applied step by step in the following order: [Optimizing Operating System Performance](../technical-guides/optimizing-operating-system-performance.md), [Optimizing Network Performance](../technical-guides/optimizing-network-performance.md), [Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md), [Post-Configuration Database Optimizations2](../technical-guides/post-configuration-database-optimizations2.md) and [General BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md). Creating dedicated filegroups for the MessageBox database and allocating these across the SAN LUNs, as described in [Optimizing Filegroups for the Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md), can provide considerable performance improvement depending on your SAN configuration and LUN layout.  
  
 To effectively determine how to scale the BizTalk Server or SQL tier, we recommend that load testing be performed using messages that approximate actual production data. Before scaling the BizTalk Server tier, ensure that SQL Server is not already a bottleneck, as recommended in [Monitoring SQL Server Performance](../technical-guides/monitoring-sql-server-performance.md). If SQL Server is not a bottleneck and there is CPU headroom on any of the BizTalk Server computers, you may be able to improve throughput by modifying your host instance layout. It is important to establish four or five key performance indicators (KPIs), which are used as high-level comparison points for all test runs. Following this advice, you will be able to quickly gauge whether a particular change degraded overall performance of the solution.  
  
 Before scaling out the SQL Server tier, apply all of the optimizations in [Optimizing Database Performance](../technical-guides/optimizing-database-performance.md). During the course of customer performance labs, the observation was that disk storage configuration for the MessageBox and TempDb databases in particular can provide over 30 percent throughput improvement. When scaling to multiple MessageBox databases, three and four MessageBox databases were used because there is little performance advantage when scaling out from a single MessageBox database to two MessageBox databases. For more information about scaling out the BizTalk Server MessageBox, see [Scaling Out the SQL Server Tier](http://go.microsoft.com/fwlink/?LinkID=158075) (http://go.microsoft.com/fwlink/?LinkID=158075) in the BizTalk Server documentation.  
  
## Implemented Optimizations  
 This section provides a checklist of all optimizations that were applied for the lab test scenarios.  
  
> [!NOTE]  
>  These should be tested in accordance with your change management procedures before applying these within your production environment.  
  
 Applying the optimizations in a systematic, controlled manner—by applying a set of optimizations, then testing the impact—will result in the maximum performance benefit. Applying optimizations without periodically testing the impact of the optimizations may actually result in a performance degradation of the solution.  
  
### Checklists of Optimizations Applied  
 **Platform and Network Optimizations**  
  
|Optimization|Reference|  
|------------------|---------------|  
|BIOS: Configure settings for performance.|[Optimizing Operating System Performance](../technical-guides/optimizing-operating-system-performance.md)|  
|Disable real-time scanning on SQL Server files.|[Optimizing Operating System Performance](../technical-guides/optimizing-operating-system-performance.md)|  
|Enable the “High performance” Power Plan on all BizTalk Server and SQL Server computers.|[General Guidelines for Improving Operating System Performance](../technical-guides/general-guidelines-for-improving-operating-system-performance.md)|  
|Disable Antivirus on all BizTalk Server and SQL Server computers.|[General Guidelines for Improving Operating System Performance](../technical-guides/general-guidelines-for-improving-operating-system-performance.md)|  
  
 **SQL Server Optimizations: General**  
  
|Optimization|Reference|  
|------------------|---------------|  
|Set NTFS File Allocation Unit to 64 KB.|[Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Install SQL Server 2008 R2.|[Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Configure SQL Server 2008 R2 Data Collector/Warehouse.|[Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Ensure that appropriate Windows privileges have been extended to the SQL Server Service accounts.|SQL Server 2008 R2: [Setting Up Windows Service Accounts](http://go.microsoft.com/fwlink/?LinkID=132144) (http://go.microsoft.com/fwlink/?LinkID=132144)|  
|Set Minimum and Maximum Server Memory for SQL Server.|[Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Grant the Windows Lock Pages In Memory privilege to the account that is used for SQL Server.|[Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Pre-size BizTalk Server databases to appropriate size with multiple data files..|[Post-Configuration Database Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|Configure SQL Server Client Protocols.|[Troubleshooting SQL Server](http://go.microsoft.com/fwlink/?LinkID=154250) (http://go.microsoft.com/fwlink/?LinkID=154250)|  
|Split the tempdb database into multiple data files of equal size on each SQL Server instance used by BizTalk Server|[Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Manually set SQL Server Process Affinity|[Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Configure MSDTC and disable DTC tracing|[Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Enable Trace Flag T1118 as a startup parameter for all instances of SQL Server|[Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
  
 **SQL Server Optimizations: BizTalk Databases**  
  
|Optimization|Reference|  
|------------------|---------------|  
|Set Autogrowth of BizTalk databases to a fixed value and not a percentage value.|[Post-Configuration Database Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|Move/split BizTalk database data and log files to separate LUNS.|[Post-Configuration Database Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|Consider setting the 'text in row' table option on specific MessageBox database tables|[Post-Configuration Database Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
  
 **BizTalk Optimizations**  
  
|Optimization|Reference|  
|------------------|---------------|  
|Separate receive ports, send ports, orchestrations, and tracking on separate, dedicated hosts.|[General BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Configure polling intervals.|[Low-Latency Scenario Optimizations2](../technical-guides/low-latency-scenario-optimizations2.md)|  
|Adjust the BizTalk configuration file maximum connection property.|“Increase the number of SOAP and HTTP concurrent connections allowed by changing the value for the maxconnection parameter” section of [General BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Define CLR Hosting parameters for each host instance on each BizTalk Server node:<br /><br /> Maximum IO Threads: 250<br /><br /> Maximum Worker Threads: 100<br /><br /> Minimum IO Threads: 25<br /><br /> Minimum Worker Threads: 25|“Define CLR hosting thread values for BizTalk host instances” section of [General BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Increase In-process messages and Internal Message Queue Size to 10000.|[Low-Latency Scenario Optimizations2](../technical-guides/low-latency-scenario-optimizations2.md)|  
|Disable BizTalk Server Group-level tracking.|[General BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Manage the number of concurrently executing requests for ASP.NET 4 Web applications that can host isolated received locations, back-end Web services and WCF services on IIS 7.5 and IIS 7.0 running in Integrated mode|[General BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Disable BizTalk Server host throttling|[General BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Configure MSDTC and disable DTC tracing|[General BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
  
 **WCF Configuration Optimizations**  
  
|Optimization|Reference|  
|------------------|---------------|  
|For each WCF service, apply the serviceThrottling service behavior, and set **maxConcurrentCalls** and **maxConcurrentSessions** to 200.|[Optimizing BizTalk Server WCF Adapter Performance](../technical-guides/optimizing-biztalk-server-wcf-adapter-performance.md)|  
|Configure the usage of serviceThrottling behavior in the backend WCF service configuration file.|[Optimizing WCF Web Service Performance](../technical-guides/optimizing-wcf-web-service-performance.md)|  
  
## See Also  
 [Scaling a Production BizTalk Server Environment](../technical-guides/scaling-a-production-biztalk-server-environment.md)