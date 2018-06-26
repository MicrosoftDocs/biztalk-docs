---
title: "Bottlenecks in the BizTalk Server Tier | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ad36897-4e4a-43b9-9cb7-0bf22bd954fb
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Bottlenecks in the BizTalk Server Tier
The BizTalk tier can be divided into the following functional areas:  
  
- Receiving  
  
- Processing  
  
- Transmitting  
  
- Tracking  
  
- Other  
  
  For these areas, if the system resources (CPU, memory, and disk) appear to be saturated, upgrade the server by scaling the platform up or out based on the characteristics of your application. If the system resources are not saturated, perform the steps described in this section.  
  
## Bottlenecks in the receive location  
 If messages build up at the receive location (for example, file receive folder grows large), this indicates that the system is unable to absorb data fast enough to keep up with the incoming load. This is due to internal throttling. That is, BizTalk Server reduces the receiving rate if the subscribers are unable to process data fast enough causing backlog buildup in the database tables. If the bottleneck is caused by hardware limitations, try scaling up. For more information about scaling up, see the following topics in the BizTalk Server 2010 documentation:  
  
- [Scaling Up the BizTalk Server Tier](http://go.microsoft.com/fwlink/?LinkId=158073) (http://go.microsoft.com/fwlink/?LinkId=158073).  
  
- [Scaling Up the SQL Server Tier](http://go.microsoft.com/fwlink/?LinkId=158077) (http://go.microsoft.com/fwlink/?LinkId=158077).  
  
  It is also possible to scale out by adding a host instance (server) to the host mapped to the receive handler. For more information about scaling out, see the following topics in the BizTalk Server 2010 documentation:  
  
- [Scaling Out the BizTalk Server Tier](http://go.microsoft.com/fwlink/?LinkId=158076) (http://go.microsoft.com/fwlink/?LinkId=158076).  
  
- [Scaling Out the SQL Server Tier](http://go.microsoft.com/fwlink/?LinkId=158075) (http://go.microsoft.com/fwlink/?LinkId=158075).  
  
  Use Perfmon to monitor the resource use on the system. It is important to confirm that the external receive location is not the cause of the bottleneck. For example, confirm whether the remote file share is saturated due to high disk I/O, the server hosting the remote outgoing queue is not saturated, or the client used to generate HTTP load is not starved on threads.  
  
## Processing bottlenecks  
 If the Host Queue – Length performance counter is climbing, it indicates that the orchestrations are not completing fast enough. For more information, see the Perfmon counter table in this topic. This could be due to memory contention or CPU saturation.  
  
 If the orchestration servers are the bottleneck, use Perfmon to identify the source.  
  
 If the server is CPU bound, consider the following:  
  
-   If the workflow is complex, consider splitting the orchestration into multiple smaller orchestrations  
  
    > [!NOTE]  
    >  Splitting an orchestration into multiple workflows can cause additional latency and add complexity. Multiple workflows can also cause an increase in the number of messages published to and consumed from the BizTalkMsgBoxDb, putting additional pressure on the database.  
  
-   If you use complex maps, consider whether they can be moved to the Receive/Send ports. Be sure to verify which ports have additional bandwidth.  
  
-   Consider scaling up the hardware or scaling out by configuring an additional processing server.  
  
## Transmitting bottlenecks  
 If the server hosting the send adapters is saturated on resources (for example, disk, memory, or CPU), consider scaling-up the server or scaling-out to additional send host servers. The sending tier could become the bottleneck if the destination (external to BizTalk) is unable to receive data fast enough. This will cause messages to buildup in the MessageBox database (Application SendHostQ).  
  
 If all the endpoints are within the scope of the topology, isolate the cause at the destination. For example, determine if the HTTP location is optimally configured to receive load. If not, consider scaling out. Also determine if the destination is growing due to excessive output messages delivered by BizTalk. If yes, you might need a maintenance plan to archive and purge the destination messages. Large numbers of files in a destination folder can severely impact the ability of the BizTalk service to commit data to the disk drive.  
  
## Tracking bottlenecks  
 The Tracking host instance is responsible for moving the Business Activity Monitoring (BAM) and Health and Activity Tracking (HAT) data from the MessageBox database (TrackingData table) to the BizTalk Tracking and/or BAM Primary Import database tables. If multiple MessageBox databases are configured, the tracking host instance uses four threads per MessageBox database.  
  
 It is possible that the Tracking host instance is CPU bound. If it is, consider scaling-up the server or scale-out by configuring an additional server with Host Tracking enabled. The multiple host instances will automatically load balance for the multiple MessageBox databases configured. For more information about scaling, see the topic [Scaling Your Solutions](http://go.microsoft.com/fwlink/?LinkId=158078) (http://go.microsoft.com/fwlink/?LinkId=158078).  
  
 If the TrackingData table in the MessageBox database grows large, it is usually because the data maintenance jobs on the BizTalk Tracking and/or BAM Primary Import database are not running as configured, causing growth of the BizTalk Tracking and/or BAM Primary Import databases. After these databases grow too large it can have a negative impact on the ability of the Tracking host to insert data into the TrackingData table. This causes tracked data to back up in the MessageBox database tables. The growth of the TrackingData table cause throttling to start.  
  
 You should only enable the minimum tracking required for your application, as this will reduce the amount of data logged and lower the risk of tracking bottlenecks. For information about disabling tracking settings for individual items such as orchestrations and send/receive ports, see [How to Disable Tracking](http://go.microsoft.com/fwlink/?LinkId=160064) (http://go.microsoft.com/fwlink/?LinkId=160064).  
  
## Other  
 Configure the deployment topology such that different functionality runs in dedicated isolated host instances. This way each host instance gets its own set of resources (for example, on a 32-bit system, 2GB virtual memory address space, handles, threads). If the server is has sufficient CPU headroom and memory to host multiple host instances, they can be configured to run on the same physical computer. If not, consider scaling out by moving the functionality to dedicated servers. Running the same functionality on multiple servers also serves to provide a highly available configuration.  
  
## BizTalk system performance counters  
  
|Object|Instance|Counter|Monitoring Purpose|  
|------------|--------------|-------------|------------------------|  
|Processor|_Total|% Processor Time|Resource Contention|  
|Process|BTSNTSvc|Virtual Bytes|Memory Leak/Bloat|  
|Process|BTSNTSvc|Private Bytes|Memory Leak/Bloat|  
|Process|BTSNTSvc|Handle Count|Resource Contention|  
|Process|BTSNTSvc|Thread Count|Resource Contention|  
|Physical Disk|_Instance|% Idle Time|Resource Contention|  
|Physical Disk|_Instance|Average Disk Queue Length|Resource Contention|  
  
### CPU contention  
 If the processor is saturated, you can fragment the application by separating the receiving from the sending and orchestration. To do this, create separate hosts, map the hosts to specific functionality (receive/send/orchestrations/tracking) and add dedicated servers to these separate hosts. Orchestration functionality is often CPU-intensive. If you configure the system so the orchestrations execute on a separate dedicated server, this can help improve overall system throughput.  
  
 If multiple orchestrations are deployed, you can enlist them to different dedicated orchestration hosts. Mapping different physical servers to the dedicated orchestration hosts ensures that the different orchestrations are isolated and do not contend for shared resources either in the same physical address space or on the same server.  
  
 Stop unused host instances. Unused host instances can compete for CPU and memory resources by regularly checking the MessageBox for messages to process. Additionally, stop unused receive locations, send ports, and orchestrations.  
  
### Spool table growth  
 Downstream bottlenecks and/or resource contention can cause the spool to start growing excessively and reduce overall performance. For more information, see “Spool Table Growth” in [How to Identify Bottlenecks in the MessageBox Database1](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md).  
  
### Memory starvation  
 High throughput scenarios can have increased demand on system memory. Since a 32-bit process is limited by the amount of memory it can consume, it is recommended to separate the receive/process/send functionality into separate host instances such that each host receives its own 2GB address space. In addition, if multiple host instances are running on the same physical server, you can upgrade to 4/8GB memory to avoid swapping data to disk from real memory. Long running orchestrations can hold onto allocated memory longer. This can cause memory bloat and throttling to start. Large messages can also cause high memory consumption.  
  
 You can ease the memory bloat problem that occurs when large messages are processed by lowering the **Internal Message Queue Size** and **In-process Messages per CPU** values for the specific host.  
  
> [!NOTE]  
>  If latency is a concern, changes to **Internal Message Queue Size** and **In-process Messages per CPU** should be made with caution as this may increase end-to-end latency of the system.  
  
### Disk contention  
 If the disks are saturated (for example, with a large number of FILE/MSMQ transports), consider upgrading to multiple spindles and striping the disks with RAID 10. In addition, whenever using the FILE transport, it is important to ensure that the receive and send folders do not grow larger than 50,000 files.  
  
 The receive folder can grow large if BizTalk Server throttles incoming data into the system. It is important to move data from the send folder so that growth in this folder does not impact the ability of BizTalk Server to write additional data. For non-transactional MSMQ queues, it is recommended to remotely create the receive queues so that disk contention is reduced on the BizTalk Server.  
  
 The remote non-transactional queue configuration also provides high availability as the remote server hosting the queue can be clustered.  
  
### Other system resource contention  
 Depending on the type of transport, it may be necessary to configure system resources like IIS for HTTP (for example, MaxIOThreads, MaxWorkerThreads).  
  
 With ASP.NET 2.0 and ASP.Net 4, the \<processModel autoConfig="true"\> setting in the machine.config file will automatically configure the following settings for optimal performance:  
  
- Maximum Worker Threads  
  
- Maximum IO Threads  
  
- minFreeThreads attribute of the httpRuntime element  
  
- minLocalRequestFreeThreads attribute of the httpRuntime element  
  
- maxConnection attribute of the \<connectionManagement\> Element (Network Settings) element  
  
  For more information about configuring parameters that affect adapter performance, see [ASP.NET Configuration Settings for the processModel Element](http://go.microsoft.com/fwlink/?LinkId=158080) (http://go.microsoft.com/fwlink/?LinkId=158080).  
  
  For more information about configuration settings that can affect BizTalk Server adapters, see [Configuration Parameters that Affect Adapter Performance](http://go.microsoft.com/fwlink/?LinkID=154200) (http://go.microsoft.com/fwlink/?LinkID=154200).  
  
  In addition to optimizing your BizTalk Server applications, other ASP.NET applications running on the same server can have an affect on overall performance. It is important to optimize all of your ASP.NET applications to reduce demand on system resources. For more information, see [ASP.NET Performance](http://go.microsoft.com/fwlink/?LinkId=158081) (http://go.microsoft.com/fwlink/?LinkId=158081).  
  
  When configuring for maximum performance, consider optimizing other external systems such as messaging engines (Message Queuing, MQSeries), applications, databases, Active Directory, etc. that are part of your overall BizTalk solution. Performance bottlenecks in any of these other external systems can have a negative effect on your BizTalk solution.  
  
### Downstream bottlenecks  
 If the downstream system is unable to receive data fast enough from BizTalk, this output data will back up in the BizTalk databases. This results in bloat, causes throttling to start, shrinks the receive pipe, and impacts the overall throughput of the BizTalk system. A direct indication of this is Spool table growth. For more information about bottlenecks and the Spool table, see [How to Identify Bottlenecks in the MessageBox Database1](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md).  
  
### Throttling impact  
 Throttling will eventually start to protect the system from reaching an unrecoverable state. Thus, you can use throttling to verify whether the system is functioning normally and discover the source of the problem. After you identify the cause of the bottleneck from the throttling state, analyze the other performance counters to determine the source of the problem. For example, high contention on the MessageBox database could be due to high CPU use, caused by excessively paging to disk that is caused by low memory conditions. High contention on the MessageBox database could also be caused by high lock contention due to saturated disk drives. While occasional throttling is not a significant threat to performance, persistent throttling can indicate a more significant underlying problem. For more information about those conditions where BizTalk Server will use throttling, see [How BizTalk Server Implements Host Throttling](http://go.microsoft.com/fwlink/?LinkID=155286) (http://go.microsoft.com/fwlink/?LinkID=155286).  
  
 For more information about how BizTalk Server throttling can help manage the use of available resources and minimize resource contention, see [Optimizing Resource Usage Through Host Throttling](http://go.microsoft.com/fwlink/?LinkID=155770) (http://go.microsoft.com/fwlink/?LinkID=155770).  
  
## BizTalk application counters  
  
|Object|Instance|Counter|Description|  
|------------|--------------|-------------|-----------------|  
|BizTalk Messaging|RxHost|Documents Received/Sec|Incoming Rate|  
|BizTalk Messaging|TxHost|Documents Processed/Sec|Outgoing Rate|  
|XLANG/s Orchestrations|PxHost|Orchestrations Completed/Sec.|Processing Rate|  
|BizTalk : MessageBox: General Counters|MsgBoxName|Spool Size|Cumulative size of all Host Queues|  
|BizTalk : MessageBox: General Counters|MsgBoxName|Tracking Data Size|Size of TrackingData table on the MessageBox|  
|BizTalk:MessageBox:Host Counters|PxHost:MsgBoxName|Host Queue - Length|Number of messages in the specific Host Queue|  
|BizTalk:MessageBox:Host Counters|TxHost:MsgBoxName|Host Queue - Length|Number of messages in the specific Host Queue|  
|BizTalk:Message Agent|RxHost|Database Size|Size of publishing (PxHost) Queue|  
|BizTalk:Message Agent|PxHost|Database Size|Size of publishing (TxHost) Queue|  
|BizTalk:Message Agent|HostName|Message Delivery Throttling State|Affects XLANG and Outbound transports|  
|BizTalk:Message Agent|HostName|Message Publishing Throttling State|Affects XLANG and Inbound transports|  
  
### Where do I start?  
 Monitoring the **Message Delivery Throttling State** and the **Message Publishing Throttling State** for each host instance is a good place to start. If the value of these counters is not zero, this indicates throttling in the BizTalk system and you can further analyze the cause of the bottleneck. For descriptions on the other performance counters, see [Bottlenecks in the Database Tier](../technical-guides/bottlenecks-in-the-database-tier.md).  
  
## Orchestration engine performance counters  
 We strongly recommend that you fine tune orchestration runtime settings because continuous orchestration dehydration\rehydration and persistence points can have a severe impact on overall performance.  You must use the following counters when testing complex orchestrations that may contain multiple persistence points and transactional scopes.  
  
|Counter|Comments|  
|-------------|--------------|  
|Orchestrations dehydrated/sec|Average number dehydrated per second.|  
|Orchestrations rehydrated/sec|Average number rehydrated per second.|  
|Persistence points/sec|Average number of orchestration instances persisted per second.|  
|Orchestrations resident in memory|Number of orchestration instances currently hosted by the host instance.|  
|Orchestrations completed/sec|Average number completed per second.|  
|Orchestrations suspended/sec|Average number suspended per second.|  
|Transactional scopes committed/sec|Average number committed per second.|  
|Transactional scopes aborted/sec|Average number aborted per second.|  
|Transactional scopes compensated/sec|Average number compensated per second.|  
  
## Backlog buildup  
 For a 1-1 deployment scenario where 1 message received results in 1 message processed and transmitted, if the outgoing rate does not equal the incoming rate, there is a backlog in the system. In this situation, you can monitor the Spool Size. When determining the cause of bottlenecks in outgoing rate, run a single use-case scenario at a time. Isolate orchestrations, receive locations, and send locations to separate hosts.  
  
 Add the BizTalk:Message Box:Host Counters to your Performance Monitor log to monitor a host. The Host Queue - Length: counter tracks the total number of messages in a particular host queue. If one or more of these counters continues grow over time, give particular attention to the artifacts executed by those hosts.  
  
 If the Spool is growing linearly, determine which Application Queue is responsible for the Spool growth.  
  
 If none of the Application Queues are growing and the Spool continues to grow, it could mean that the purge jobs are unable to keep up. This occurs if the agent is not running or there is other system resource contention on the SQL Server.  
  
 If one of the Application Queues is growing, diagnose the cause of this growth. Monitor the system resources on the system that is unable to drain the specific Application Queue (for example, Orchestration Host-Q is growing due to CPU starvation on the server). In addition, verify the values of the throttling counter for the specific host instance.  
  
 If the BizTalk:Messsage Agent Message Delivery Throttling State and Message Publishing Throttling State performance counters are not zero, check the value to confirm the reason for throttling (for example, memory threshold exceeded, in-flight message count too high, and so on).  
  
## Stand-Alone Profiler  
 You can use performance counters to detect the location of the bottleneck at a high level. However, once narrowed down, you might need to examine the code more closely to help ease the problem. The Stand-Alone Profiler that ships with Visual Studio 2010 can be a very helpful tool to help diagnose where the code is spending most of its cycles. For more information, see  
  
## L2/L3 cache  
 From a hardware perspective, you can gain the biggest benefits by using the onboard CPU cache. Higher CPU cache helps increase cache hit rate reducing the need for the system to page data in and out of memory to disk.  
  
## 64-Bit performance bottlenecks  
 Performance on 64-bit systems may appear lower than what can be achieved on 32-bit systems. This is possible for a few reasons, the most important one being memory.  
  
 Measuring performance on a 32-bit system with 2 GB of memory and comparing the results to a similar 64-bit system with 2 GB of memory is not comparing the same thing. The 64-bit system will appear to be disk-I/O bound (low % Disk Idle time & high Disk Queue Length) and CPU bound (max CPU and high context switching). However, this is not because performing file I/O on a 64-bit system is more expensive.  
  
 The 64-bit system is more memory intensive (64-bit addressing) which results in the operating system consuming most of the 2 GB available memory. When this happens, most other operations cause paging to disk which stresses the file subsystem. Therefore, the system spends CPU cycles paging in/out of memory both data and code and is impacted by the high disk latency cost. This manifests itself as both higher disk contention and higher CPU consumption.  
  
 The way to alleviate this problem is to scale-up the server by upgrading the memory. Scaling-up to 8 GB is idea, however, adding more memory will not help improve throughput unless the source of the problem is CPU starvation due to low memory conditions.  
  
## Using BAM to identify bottlenecks and high-latency issues  
 When low-latency is important, you can use BAM to measure the time the system takes to complete each stage within the BizTalk Server system. Although you can use HAT to debug the state of messages and diagnose the source of problems in routing messages, you can use BAM to track various points through the message flow. By creating a BAM tracking profile that defines an activity with continuations, you can measure latency between different parts of the system to help track the most expensive stages within the workflow process.  
  
 You can use Orchestration Debugger in HAT to query a suspended instance, resume the instance in debug mode, and add appropriate breakpoints using the Technical Details View. This will enable you to trace the activities and debug messages step by step.  
  
 You can set breakpoints to track the following events:  
  
- The start and finish of an orchestration  
  
- The start and finish of a shape  
  
- The sending or receipt of a message  
  
- Exceptions  
  
  At each breakpoint, you can examine information about local variables, messages and their properties, ports, and role links.  
  
## See Also  
 [Finding and Eliminating Bottlenecks](../technical-guides/finding-and-eliminating-bottlenecks.md)