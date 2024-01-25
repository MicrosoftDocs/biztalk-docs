---
description: "Learn more about: Investigating Bottlenecks"
title: "Investigating Bottlenecks"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Investigating Bottlenecks
This topic describes a recommended process for investigating bottlenecks.

## What is the source of the problem?
 The source of the bottleneck could be hardware or software related. When resources are underused, it is usually an indication of a bottleneck. Bottlenecks can be caused by hardware limitations, by inefficient software configurations, or by both.

 Identifying bottlenecks is an incremental process whereby alleviating one bottleneck can lead to the discovery of the next one. The science of identifying and alleviating these bottlenecks is the objective of this topic. It is possible for a system to perform at peaks for short periods of time. However, for sustainable throughput a system can only process as fast as its slowest performing component.

## Using an iterative approach to testing
 Bottlenecks can occur at the endpoints (entry/exit) of the system or in the middle (orchestration/database). After the bottleneck has been isolated, use a structured approach to identify the source. After the bottleneck is eased, it is important to measure performance again to ensure that a new bottleneck has not been introduced elsewhere in the system.

 The process of identifying and fixing bottlenecks should be done in an iterative manner. Vary only one parameter at a time, repeat exactly the same steps during each test run, and then measure performance to verify the impact of the single modification. Varying more than one parameter at a time could conceal the effect of the change.

 For example, changing parameter 1 could improve performance. However, changing parameter 2 in conjunction with changing parameter 1 could have a detrimental effect and negate the benefits of changing parameter 1. This leads to a net zero effect and results in a false negative on the effect of varying parameter 1 and a false positive on the effect of varying parameter 2.

## Testing consistency
 Measuring performance characteristics after changing settings should be done to validate the effect of the change.

-   **Hardware -** Use consistent hardware because varying the hardware can cause inconsistent behavior and produce misleading results. For example, you would not use a laptop to test performance of a BizTalk solution.

-   **Test Run Duration -** Measure performance for a fixed minimum period to ensure that the results are sustainable. Running tests for longer periods also ensures the system has gone through the initial warm/ramp up period where all caches are populated, database tables have reached expected counts, and throttling is given sufficient time to regulate throughput once predefined thresholds are hit. This approach will help discover optimal sustainable throughput.

-   **Test Parameters –** Do not vary test parameters from test run to test run. For example, varying map complexity and/or document sizes can produce different throughput and latency results.

-   **Clean State -** After a test is complete, ensure that the state of the test environment is clean before running the next test. For example, historical data can build up in the database affecting run-time throughput. Recycling the service instances helps to release cached resources like memory, database connections, and threads. In your test environment, you may want to create and execute the bts_CleanupMsgbox stored procedure as described in [How to Manually Purge Data from the MessageBox Database in a Test Environment](../core/how-to-manually-purge-data-from-the-messagebox-database-in-a-test-environment.md) (https://go.microsoft.com/fwlink/?LinkId=158064). This script is intended to return your BizTalk Server test environment to a fresh state with regards to the Message Box between runs. The script deletes all running instances and all information about those instances including state, messages, and subscriptions, but leaves all activation subscriptions so you do not have to re-enlist your orchestrations or send ports. Note that this tool is not supported on production systems.

-   **Performance Testing and Tuning -** The goal of this test category is to maximize performance and throughput of your application and find the Maximum Sustainable Throughput (MST) of your system.  For more information about planning and measuring Maximum Sustainable Performance see [Planning for Sustained Performance](../core/planning-for-sustained-performance.md) (https://go.microsoft.com/fwlink/?LinkId=158065) and [What Is Sustainable Performance?](../core/what-is-sustainable-performance.md) (https://go.microsoft.com/fwlink/?LinkId=132304).

     The MST is the highest load of message traffic that a system can handle indefinitely in a production environment. All BizTalk applications should be tested for performance and throughput before going into production. At a minimum, you should run a representative set of test cases that represent the most common usage scenarios. We recommend that you test against expected loads and peak loads in a separate environment that matches characteristics of the production environment. This environment should have all of the corporate standard services installed and running, such as monitoring agents, and antivirus software.

-   We also recommend that you test new BizTalk applications on the same hardware in production alongside the other BizTalk applications that are running. These other BizTalk applications put additional load on the BizTalk Server, SQL Server, network I/O, and disk I/O. In addition, one BizTalk application could cause another to throttle (when the spool depth gets too large, for example). All BizTalk applications should be performance / stress tested before going into production. In addition, you should determine how long it takes the system to recover from peak loads. If the system does not fully recover from a peak load before the next peak load occurs, then you've got a problem. The system will get further and further behind and will never be able to fully recover.

## Expectations: throughput vs. latency
 You can expect a certain amount of throughput and/or latency from the deployed system. Attempting to achieve high throughput and low latency simultaneously places opposing demands on the system. You can expect optimal throughput with reasonable latency. As throughput improves, stress (such as, higher CPU consumption, higher disk-I/O contention, memory pressure, and greater lock contention) on the system increases. This situation can have a negative impact on latency. To discover optimal capacity of a system, we recommend that you identify and minimize any bottlenecks.

 Completed instances residing in the database can cause bottlenecks. When bottlenecks occur, performance can degrade. Giving the system sufficient time to drain can help fix the problem. Discovering the cause of the backlog buildup and helping fix the issue is important.

 To discover the cause of the backlog, you can analyze historical data and monitor performance counters (to discover usage patterns, and diagnose the source of the backlog). Commonly, backlogs can occur when large volumes of data are processed in a batched manner on a nightly basis. You may find it useful to discover the capacity of the system and its ability to recover from a backlog. This information can help you to estimate hardware requirements for handling overdrive scenarios and the amount of buffer room to accommodate within a system to handle unforeseen spikes in throughput.

 Monitoring performance counters can help individuate potential bottlenecks that could arise at runtime. However, when we suspect that the culprit of CPU or memory bottleneck may be one of the custom components that compose the solution, we strongly recommend that you use profiling tools such Visual Studio Profiler or ANTS Performance Profiler during a performance test to narrow and individuate with certainty the class that generates the problem. Obviously, profiling an application interferes with performance. Therefore, these tests should be focused on individuating those components that cause memory consumption, CPU utilization or latency and figures collected during these tests should be discarded.

 Tuning the system for optimal sustainable throughput requires an in depth understanding of the deployed application, the strengths and weaknesses of the system, and usage patterns of the specific scenario. The only way to discover bottlenecks and predict optimal sustainable throughput with certainty is through thorough testing on a topology that closely matches what will be used in production. When running load and stress tests against a certain use case, isolating single artifacts (receive locations, send ports, orchestrations) into separate host instances and setting the right counters inside the performance monitor tool is crucial to narrow down the cause of a bottleneck.

 Other topics in this section guide you through the process of defining that topology, and provide guidance on how to lessen and avoid bottlenecks.

## Scaling
 Bottlenecks can occur at various stages of a deployed topology. Some bottlenecks can be addressed by either scaling up or scaling out the environment. Scaling up is the process of upgrading the existing computer. For example, you can upgrade a BizTalk Server computer from a four-processor computer to an eight-processor computer, as well as substituting the existing CPUs and adding more RAM. In this way, you can accelerate resource-intensive tasks such as document parsing and mapping. Scaling out is the process of adding servers to your deployment. The decision to scale up or out depends on the type of bottleneck and the application being configured. An application needs to be built from the ground up to be capable of taking advantage of scaling up or out. The following guidance explains how to change hardware deployment topologies based on bottlenecks encountered.

 **Scaling up** means running a BizTalk solution on upgraded hardware (for example, adding CPU’s and memory). You should look at scaling up when 1) scaling out is too expensive or 2) scaling out will not help solve a bottleneck. For example, you can significantly reduce the time spent transforming and processing a large message if you run the task on a faster machine.

 **Scaling out** the application platform consists of adding BizTalk nodes to the BizTalk Server Group and using them to run one or more parts of the solution. You should look at scaling out when 1) you need to isolate send, receive, processing, tracking hosts or 2) when memory, I/O or Network I/O resources are maxed out for a single server. The load can be spread across multiple servers; however, adding new nodes to the BizTalk Server Group can increase the lock contention on the MessageBox database.

 So should you scale up or scale out? Scaling up your platform can reduce the latency of a BizTalk solution because it makes single tasks (for example, message mapping) run faster. Scaling out can improve the maximum sustainable throughtput and the scalability of your BizTalk solution because it allows you to spread the workload across multiple machines.

## See Also
 [Finding and Eliminating Bottlenecks](../technical-guides/finding-and-eliminating-bottlenecks.md)