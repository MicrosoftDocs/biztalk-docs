---
title: "Host Throttling Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "host throttling, performance counters"
ms.assetid: b9090d1c-86be-40db-b814-cc116a426d95
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Host Throttling Performance Counters
This section describes the performance monitor counters that measure system parameters that impact host throttling. The following performance counters are accessible for each host instance under the **BizTalk:Message Agent** performance object category:  
  
|Counter|Description|  
|-------------|-----------------|  
|Active instance count|Number of service instances active in memory. For the orchestration engine, a service instance refers to each running instance of an orchestration schedule. For the End Point Manager, a service instance may either correspond to a single stateless message, or to a collection of stateful messages. **Note:**  Stateful instances are those that maintain certain state information about the messages associated with the instance. Messages belonging to a stateful instance are co-related in some form or the other. For example an ordered send port that maintains information about the ordering are considered stateful instances. Most messaging scenarios involve stateless instances where messages are processed completely independent of each other. Each such stateless instance corresponds to a single message within the EPM.|  
|Database session|Number of concurrent MessageBox database connections being used.|  
|Database session threshold|The current threshold for concurrent database sessions. This is initially set to the **Database connections** value on the **Resource-Based Throttling** tab in **Settings Dashboard**. This value is auto-tuned based on the database session usage of the process. If the number of concurrent database sessions exceeds this threshold at any time, host throttling is implemented.|  
|Database size|Number of messages in the database queues that this process has published. This value is measured by the number of items in the queue tables for all hosts and the number of items in the spool and tracking tables. If a process is publishing to multiple queues, this counter reflects the weighted average of all the queues. **Note:**  If the host is restarted, statistics held in memory are lost. Since there is some overhead involved, BizTalk Server will resume gathering statistics only when there are at least 100 publishes with 5% of the total publishes within the restarted host process.|  
|High database session|-   0: Normal<br />-   1: Database session count exceeds threshold|  
|High database size|-   0: Normal<br />-   1: Database size has grown beyond threshold<br /><br /> This counter will be set to a value of one if either of the conditions listed for the **Message count in DB** threshold occurs. [How to Modify Resource Based Throttling Settings](../core/how-to-modify-resource-based-throttling-settings.md) provides information on this throttling threshold.|  
|High in-process message count|-   0: Normal<br />-   1: In-process message count exceeds limit|  
|High message delivery rate|-   0: Normal<br />-   1: Message delivery rate exceeds the message processing Rate|  
|High message publishing rate|-   0: Normal<br />-   1: Publishing request rate exceeds completion rate|  
|High process memory|-   0: Normal<br />-   1: Process memory exceeds threshold|  
|High system memory|-   0: Normal<br />-   1: System memory exceeds threshold|  
|High thread count|-   0: Normal<br />-   1: Thread count exceeds threshold|  
|In-process message count|Number of in-memory messages delivered to the XLANG engine or the outbound messaging engine that are not yet processed.|  
|In-process message count threshold|The current threshold for in-process message count.|  
|Message delivery delay (ms)|The current delay in ms imposed on each message delivery batch (applicable if the message delivery is being throttled).|  
|Message delivery incoming rate|Number of messages per second that are being delivered to the Orchestration engine or the Messaging engine in the given sample interval.|  
|Message delivery outgoing rate|Number of messages per second that are being processed by the Orchestration engine or the Messaging engine in the given sample interval.|  
|Message delivery throttling state|A flag indicating whether the system is throttling message delivery (affecting XLANG message processing and outbound transports).<br /><br /> -   0: Not throttling<br />-   1: Throttling due to imbalanced message delivery rate (input rate exceeds output rate)<br />-   3: Throttling due to high in-process message count<br />-   4: Throttling due to process memory pressure<br />-   5: Throttling due to system memory pressure<br />-   9: Throttling due to high thread count<br />-   10: Throttling due to user override on delivery|  
|Message delivery throttling state duration|Seconds since the system entered this state. If the host is throttling, how long it has been throttling; if it is not throttling, how long since throttling was applied.|  
|Message delivery throttling user override|This counter reflects the user override that is monitored by the engine and interpreted as follows:<br /><br /> -   0: No override<br />-   1: Always throttle message delivery<br />-   2: Do not throttle message delivery<br /><br /> This override is configurable in the **Rate-Based Throttling** tab in **Settings Dashboard**.|  
|Message publishing delay (ms)|The current delay in ms imposed on each message publishing batch (applicable if the message publishing is being throttled and if the batch is not exempted from throttling).|  
|Message publishing incoming rate|Number of messages per second that are being sent to the database for publishing in the given sample interval.|  
|Message publishing outgoing rate|Number of messages per second that are actually published in the database in the given sample interval.|  
|Message publishing throttling state|A flag indicating whether the system is throttling message publishing (affecting XLANG message processing and inbound transports).<br /><br /> -   0: Not throttling<br />-   2: Throttling due to imbalanced message publishing rate (input rate exceeds output rate)<br />-   4: Throttling due to process memory pressure<br />-   5: Throttling due to system memory pressure<br />-   6: Throttling due to database growth<br />-   8: Throttling due to high session count<br />-   9: Throttling due to high thread count<br />-   11: Throttling due to user override on publishing|  
|Message publishing throttling state duration|Seconds since the system entered this state. If the host is throttling, how long it has been throttling; if it is not throttling, how long since throttling was applied.|  
|Message publishing throttling user override|This counter reflects the user override that is monitored by the engine and interpreted as follows:<br /><br /> -   0: No override<br />-   1: Always throttle message publishing<br />-   2: Do not throttle message publishing<br /><br /> This override is configurable in the **Rate-Based Throttling** tab in **Settings Dashboard**.|  
|Physical memory usage (MB)|The amount of physical memory in MB being used on the machine by all processes.|  
|Process memory usage (MB)|The process memory consumption in MB. This is the maximum of the process’s working set size and the total space allocated for the page file for the process.|  
|Process memory usage threshold (MB)|The current threshold for process memory consumption in MB. This is initially set to the **Process virtual** value in **Settings Dashboard**. If a percentage value is specified, it is computed based on the available memory to commit|  
|Service class ID|The decimal value of the initial part of the service class GUID that this performance counter instance corresponds to. A process may host more than one service class and the message agent performance counters show the data for the most active service class.|  
|Thread count|Number of threads being used within the process.|  
|Thread count threshold|The current threshold for the number of threads in the process. This is initially set to the **Threads** value on the **Resource-Based Throttling** tab in **Settings Dashboard**. This value is auto-tuned depending on the thread requirements of the current process. If the number of threads in the process exceeds this threshold value at any point in time, host throttling is implemented.|  
|Total batches committed|Number of database batches that the service class has committed.|  
|Total messages delivered|Number of outbound messages delivered to the Orchestration engine or the End Point Manager (EPM).|  
|Total messages published|Number of messages published.|  
  
> [!NOTE]
>  The **BizTalk:Message Agent** performance counters are provided for the explicit purpose of analyzing the throttling behavior of a host and therefore will not capture data unless the specified host is actively processing documents. This behavior is by design to prevent consuming system threads with performance monitor when throttling activities are not occurring.  
  
## To access performance counters  
 Use the following steps to access the performance counters.  
  
#### If you are using Windows 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:Message Agent** performance counter object and select the counters to be monitored.  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.  To select all available counter instances, select \<**All instances**>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.  
  
## See Also  
 [Throttling Design Recommendations](../core/throttling-design-recommendations.md)   
 [How BizTalk Server Implements Host Throttling](../core/how-biztalk-server-implements-host-throttling.md)   
 [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)