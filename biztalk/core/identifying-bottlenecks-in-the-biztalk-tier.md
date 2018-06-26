---
title: "Identifying Bottlenecks in the BizTalk Tier | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f38ade78-8af3-4485-9b2a-5e4cdba965d2
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Identifying Bottlenecks in the BizTalk Tier
The BizTalk tier can be divided into the following functional areas:  
  
- Receiving  
  
- Processing  
  
- Transmitting  
  
- Tracking  
  
- Other  
  
  For these areas, if the system resources (CPU, memory, and disk) appear to be saturated, upgrade the server by scaling up. If the system resources are not saturated, perform the steps described in this section.  
  
## Bottlenecks in the Receive Location  
 If messages start building up at the receive location (for example, file receive folder grows large or outgoing queue is not being drained fast enough) this is an indication that the system is unable to absorb data at a sufficiently fast rate to keep up with the incoming load either due to internal throttling (BizTalk reduces receiving rate if the subscribers are unable to process data fast enough causing backlog buildup in the database tables). In case the bottleneck is caused due to hardware limitations try scaling up. It is also possible to scale out by adding a Host Instance (server) to the Host mapped to the receive handler. Use Perfmon to monitor the resource utilization on the system. It is important to confirm that the external receive location is not the cause of the bottleneck. For example, remote file share is saturated due to high disk IO or the server hosting the remote outgoing queue is not saturated or the client used to generate HTTP/SOAP load is not starved on threads.  
  
## Processing Bottlenecks  
 If the Host Queue - Length count (see the Perfmon counter table below) is climbing, it indicates that the orchestrations are not completing fast enough. This could be due to memory contention or CPU saturation.  
  
 If the orchestration servers are the bottleneck, use Perfmon to identify the source.  
  
 If the server is CPU bound, consider the following:  
  
-   If the workflow is complex consider splitting the orchestration into multiple smaller orchestrations  
  
    > [!NOTE]
    >  Splitting an orchestration into multiple workflows can cause additional latency and add complexity.  
  
-   If complex maps are used consider whether they can be moved to the Receive/Send ports (verify which ports have additional bandwidth).  
  
-   Consider scaling up the hardware or if possible consider scaling out by configuring an additional processing server.  
  
## Transmitting Bottlenecks  
 If the transmitting server is saturated on resources (for example, disk, memory, CPU), consider scaling-up the server or if possible consider scaling-out to additional send host servers. The sending tier could become the bottleneck if the destination (external to BizTalk) is unable to receive data fast enough. This will cause messages to buildup in the MessageBox database (Application SendHostQ).  
  
 If at all the endpoints are within the scope of the topology, consider isolating the cause at the destination. For example, is the HTTP/SOAP location optimally configured to receive load or could it be scaled-out? Is the destination growing due to excessive output messages delivered by BizTalk? If yes, consider a maintenance plan to archive and purge the destination messages. For example, large numbers of files in a destination folder can severely impact the ability of the BizTalk service to commit data to the disk drive.  
  
## Tracking Bottlenecks  
 The Tracking Host Instance is responsible for moving both BAM & tracked message event and service instance data from the MessageBox database (TrackingData table) to the BizTalkDTADb and/or BAMPrimaryImport database tables. If multiple MessageBox databases are configured the tracking host instance uses four threads per MessageBox.  
  
 It is possible that this host instance could get CPU bound. If that is the case consider scaling-up the server or scale-out by configuring an additional server with Host Tracking enabled. The multiple host instances will automatically balance load for the multiple MessageBoxes configured.  
  
 If the TrackingData table in the MessageBox database starts backing up, it is usually because the data maintenance jobs on the BizTalkDTADb and/or BAMPrimaryImport database are not running as configured causing growth of the BizTalkDTADb and/or BAMPrimaryImport database. Once these databases grow too large it can have a negative impact on the ability of the tracking host to insert data into these tables causing the tracked data to backup in the MessageBox database tables. The growth of the MessageBox->TrackingData table will cause throttling to kick in.  
  
## Other  
 Configure the deployment topology such that different functionality runs in dedicated isolated host instances. This way each host instance gets its own set of resources (on a 32-bit system, 2GB virtual memory address space, handles, threads). If the server is powerful enough (sufficient CPU headroom, memory) to host multiple host instances they can all be configured to run on the same physical machine. If not, this also makes it easy to scale-out by moving the functionality to dedicated servers. Running the same functionality on multiple servers also serves to provide a highly available configuration.  
  
## BizTalk System Performance Counters  
  
|Object|Instance|Counter|Monitoring Purpose|  
|------------|--------------|-------------|------------------------|  
|Processor|_Total|% Processor Time|Resource Contention|  
|Process|BTSNTSvc|Virtual Bytes|Memory Leak/Bloat|  
|Process|BTSNTSvc|Private Bytes|Memory Leak/Bloat|  
|Process|BTSNTSvc|Handle Count|Resource Contention|  
|Process|BTSNTSvc|Thread Count|Resource Contention|  
|Physical Disk|_Total|% Idle Time|Resource Contention|  
|Physical Disk|_Total|Current Disk Queue Length|Resource Contention|  
  
### CPU Contention  
 If the processor is saturated consider fragmenting the application by separating the Receiving from the Sending and Orchestration. The way to accomplish this is by creating separate hosts, mapping these hosts to specific functionality (Receive/Send/Orchestrations/Tracking) and adding dedicated servers to these separate hosts. Orchestration functionality is generally known to be CPU hungry, thus configuring the system such that the orchestrations execute on a separate dedicated server helps improve overall system throughput.  
  
 If multiple orchestrations are deployed, it is possible to enlist them to different dedicated Orchestration-Hosts. Mapping different physical servers to the dedicated Orchestration-Hosts ensures that the different orchestrations are isolated and do not contend for shared resources either in the same physical address space or on the same server.  
  
### Memory Starvation  
 High throughput scenarios can have increased demand on system memory. Since a 32-bit process is limited by the amount of memory it can consume, it is recommended to separate the Receive/Process/Send functionality into separate Host Instances such that each host receives its own 2GB address space. In addition, if multiple Host Instances are running on the same physical server it is useful to upgrade to 4/8GB memory to avoid having to swap data to disk from real memory. Long running orchestrations can hold onto allocated memory longer causing memory bloat and thus throttling to kick in. Large messages can also cause high memory consumption.  
  
 It is possible to overcome this memory bloat problem when large messages are being processed by lowering the **Internal Message Queue Size** and **In-process Messages per CPU** values for the specific host.  
  
### Disk Contention  
 If the disks are saturated (for example, File/MSMQ transports) consider upgrading to multiple spindles and striping the disks with RAID 1+0. In addition whenever using the FILE transport it is important to ensure that the folders (both Receive and Send) do not grow too large (>50,000 files).  
  
 The Receive folder can grow large if BizTalk Server chooses to throttle incoming data into the system due to various reasons mentioned below. It is also important to move data from the send folder so that growth in this folder does not impact the ability of BizTalk Server to write additional data. For non-transactional MSMQ queues, it is recommended to remotely create the receive queues so that disk contention is reduced on the BizTalk server.  
  
 This configuration (remote non-transactional queues) also provides the added benefit of high availability as the remote server hosting the queue can be clustered.  
  
### Other System Resource Contention  
 Depending on the nature of the transport configured it may be necessary to configure system resources like IIS for HTTP/SOAP (for example, MaxIOThreads, MaxWorkerThreads).  
  
### Downstream Bottlenecks  
 If the downstream system is unable to receive data fast enough from BizTalk this output data will back up within the BizTalk databases resulting in bloat causing throttling to kick in shrinking the receive pipe thereby impacting the overall throughput of the BizTalk system. A direct indication of this would be Spool growth.  
  
### Throttling Impact  
 Throttling will ultimately kick in to protect the system from reaching an unrecoverable state. Thus throttling is a good place to verify whether the system is functioning normally and discover the source of the problem. After the cause of the bottleneck has been identified from the throttling state, analyze the other performance counters to drill down into the source of the problem.  
  
 For example, high contention on the MessageBox database could be due to high CPU usage, which could be caused due to excessively paging to disk which could be caused due to low memory conditions. High contention on the MessageBox could also be caused due to high lock contention which could be due to saturated disk drives.  
  
## BizTalk Application Counters  
  
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
 Monitoring the **Message Delivery Throttling State** and the **Message Publishing Throttling State** for each host instance is usually a good place to start. If the value of these counters is not zero it is indicative that throttling is happening within the BizTalk system and it is possible to further analyze the cause of the bottleneck. For descriptions on the other performance counters, see [Identifying Bottlenecks in the Database Tier](http://msdn.microsoft.com/library/f1dc58b5-73b0-41b5-9a1e-c0698485c732).  
  
## Backlog Buildup  
 For a 1-1 deployment scenario where 1 message received results in 1 message processed and transmitted, if the Outgoing Rate does not equal the Incoming Rate, a backlog is building up somewhere in the system. For such a situation it is possible to monitor the Spool Size.  
  
 If the Spool is growing linearly, it is possible to further drill down by verifying which Application Queue is responsible for the Spool growth.  
  
 If none of the application queues are growing and the Spool continues to grow it could mean that the purge jobs are unable to keep up either due to the agent not running or other system resource contention on the SQL server.  
  
 If one of the application queues are growing, it is important to diagnose the cause of this growth. Monitor the system resources on the system that is unable to drain the specific application queue (for example, Orchestration Host-Q is growing due to CPU starvation on the server). In addition verify the values of the throttling counter for the specific host instance.  
  
 If the Delivery/Publishing State is not zero, check the value to confirm the reason for throttling (for example, memory threshold exceeded, in-flight message count too high etc.).  
  
## F1 Profiler  
 By using performance counters, it is possible to quickly detect at a high level the location of the bottleneck. However, once narrowed down, it may be necessary to drill down further into the code to help alleviate the problem. The F1 Profiler that ships with Visual Studio can be a very helpful tool to help diagnose where the code is spending most of its cycles.  
  
 Symbols are important to help with creating a more meaningful stack (especially for unmanaged code). For example, the F1-Profiler can help pinpoint the number of invocations and the amount of time an API call takes to return. Drilling further down the stack, it may be possible to detect the underlying cause of the high latency. It could be a blocking call to a database query or simply a call to wait on an event.  
  
## L2/L3 Cache  
 The biggest benefits (from a hardware perspective) that can be gained is by utilizing onboard CPU cache. Higher CPU cache helps increase cache hit rate reducing the need for the system to page data in and out of memory to disk.  
  
## 64-Bit Performance Bottlenecks  
 Performance on 64-bit systems may appear lower than what can be achieved on 32-bit systems. This is possible due to a couple of reasons, the most important one being memory.  
  
 Measuring performance on a 32-bit system with 2-GB of memory and comparing the results to what can be achieved on a similar 64-bit system with 2-GB of memory is not a true apples to apples comparison. The 64-bit system will appear to be disk-IO bound (low % Disk Idle time & high Disk Queue Length) and CPU bound (max CPU & high Context Switching). However, this is not because performing file IO on a 64-bit system is more expensive.  
  
 The 64-bit system is more memory hungry (64-bit addressing) which results in the OS consuming most of the 2-GB available memory. Once this happens most other operations cause paging to disk which stresses the file subsystem. The system now not only spends CPU cycles paging in/out of memory both data and code but is also impacted by the high disk latency cost. This manifests itself as both higher disk contention and higher CPU consumption.  
  
 The way to alleviate this problem is to scale-up the server by upgrading the memory (ideally 8-GB). However, adding more memory will not help improve throughput unless the source of the problem is CPU starvation due to low memory conditions.  
  
## Using BAM to identify bottlenecks and high latency issues  
 In situations where low latency is important, you can use BAM to measure the time the system takes to complete each stage within the BizTalk system. Although  tracked message event and service instance data can be used to debug the state of messages and diagnose the source of problems in routing messages, BAM can be used to track various points through the message flow. By creating a BAM tracking profile (defining an activity with continuations), you can measure latency between different parts of the system to help track the most expensive stages within the workflow process.