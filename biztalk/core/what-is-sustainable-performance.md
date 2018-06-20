---
title: "What Is Sustainable Performance? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "reliability, sustainable performance"
  - "performance, goals"
  - "performance, sustainable performance"
  - "planning, performance"
  - "performance, planning"
  - "sustainable performance"
ms.assetid: 4b18b976-7714-431f-8976-f40a1016d5f3
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is Sustainable Performance?
When planning for and estimating system sustainability, it is critical to think in terms of sustainability over the long term. The primary considerations are:  
  
- **Load Profiles and Performance Goals**: You can't have too much detail when it comes to load profiles and performance goals. Testing and readiness certification will be based on being able to handle these loads long term.  
  
- **Other Activities and Processes that Compete for Server Resources**: It isn’t just about the message load. There are other processes and activities taking place on the servers that affect performance such as database maintenance and MessageBox queries.  
  
- **Planned and Unplanned System Outages and Downtime**: Floodgate events and message backlog can change the effective load profile.  
  
  When thinking about building sustainable systems and the tests to certify them, be sure to take these factors into account and plan for them.  
  
## Is Your Performance Sustainable?  
 When discussing performance for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], we define maximum sustainable performance as follows:  
  
- The highest load of message traffic that a system can handle indefinitely in a production environment.  
  
  While this seems simple, there are many factors that you must consider when evaluating whether or not a solution - running on a particular set of hardware - will be able to support the loads experienced day in and day out after you put the solution into production.  
  
  Before you put your solution into production, consider the following factors to evaluate whether the solution can handle the highest load of message traffic indefinitely:  
  
- Desired Performance Goals and Throughput/Latency profiles.  
  
- Other Processes Running on the Same Hardware such as:  
  
  -   Normal Monitoring and Troubleshooting  
  
  -   Operational database maintenance such as log shipping, backup, purging, index maintenance, and statistics updates.  
  
  -   Other Applications  
  
- Planned and Unplanned System Outages such as:  
  
  -   Partner sites down which blocks sending or receiving messages  
  
  -   Regular system maintenance down time  
  
## Know Your Performance Goals  
 Before you can evaluate your solution for sustainability, you must have a detailed understanding of the expected production loads. Without a well understood goal, you can't evaluate readiness. A well formed set of performance goals is critical as it will drive your strategies around system testing and certification. Your performance goals should have the following elements:  
  
-   A curve that defines performance as a function of time. These functions can range from extremely simple to very complex.  
  
-   A performance requirement associated with the performance function.  
  
-   A distribution of file sizes and types.  
  
### Example 1  
  
-   Each day, messages build up from 0 msgs/sec at 8:00AM to 80 msgs/sec at noon and then back down to 0 msgs/sec at 9:00PM, roughly in the form of a bell curve.  
  
-   The system has no specific latency requirement for each message, but it must be able to process this load, plus all of the previous day’s message load (for example, in the event of a 24 hour system outage) without getting behind.  
  
-   There are three document types: Sales Basket, Back Order, and Stock Request. Sales Basket documents range in size between 2 and 10 kilobytes and make up 75% of the message counts at any given time. Back Order and Stock Request documents are always close to 1 Kilobyte in size and make up the remaining, 10% and 15% of the message count at any given time, respectively.  
  
### Example 2  
  
-   Every night at midnight, a batch of 500,000 messages arrive for processing.  
  
-   All messages in the batch must be processed to completion in 8 hours.  
  
-   All messages are of the same type and are evenly distributed between 10 and 50 Kilobytes, inclusive. In addition, the batch always contains 10 catalog type messages that are 10 megabytes each and must be subdivided into individual catalog entries for processing.  
  
### Example 3  
  
-   Every morning at 8:00AM, 4000 customer service representatives log on to the interactive system and perform, on average, 4 inquiries per representative per minute until closing time at 5:00PM, 7 days per week.  
  
-   All inquiries must return results in less than 2 seconds.  
  
-   All inquiries are the same type and are evenly distributed between 500 and 1000 bytes in size, inclusive.  
  
#### A performance requirement associated with the performance function  
 Continuing with the above examples:  
  
-   **Example 1 (continued)**:  The system has no specific latency requirement for each message, but it must be able to process this load, plus all of the previous day’s message load (for example,, in the event of a 24 hour system outage) without getting behind.  
  
-   **Example 2 (continued)**:  All messages in the batch must be processed to completion in 8 hours.  
  
-   **Example 3 (continued)**:  All inquiries must return results in less than 2 seconds.  
  
#### A distribution of file sizes and types  
  
-   **Example 1 (continued)**: There are three document types: Sales Basket, Back Order, and Stock Request. Sales Basket documents range in size between 2 and 10 kilobytes and make up 75% of the message counts at any given time. Back Order and Stock Request documents are always close to 1 Kilobyte in size and make up the remaining, 10% and 15% of the message count at any given time, respectively.  
  
-   **Example 2 (continued)**: All messages are of the same type and are evenly distributed between 10 and 50 Kilobytes, inclusive. In addition, the batch always contains 10 catalog type messages that are 10 megabytes each and must be subdivided into individual catalog entries for processing.  
  
-   **Example 3 (continued)**: All inquiries are the same type and are evenly distributed between 500 and 1000 bytes in size, inclusive.  
  
## Accounting for Other Processes  
 In addition to the load profiles that pass directly through the BizTalk engine, there are always other processes that compete for resources on the same hardware.  These other processes will reduce the overall sustainable performance capabilities of the system. Database maintenance is probably the most common example of this type of process.  
  
 Every database, large or small, requires periodic operational maintenance such as log shipping, backup, archive, and purging. Monitoring and troubleshooting are other examples of operations that you must take into account when defining and certifying what is sustainable. For example, querying the MessageBox (for example, via the administration console Group Hub page) to see how many messages of a given type have been suspended in the last 24 hours requires resources from SQL Server that could otherwise have been used to process messages.  
  
 Following is a list of activities that will typically have the most effect on overall sustainability in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
- **Log Shipping and Backup**. As part of most disaster recovery plans involving SQL Server, you must perform log shipping and backup periodically for all of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group databases. For more information, see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md). Also see [Log Shipping](../core/log-shipping.md).  
  
- **Archiving and Purging Tracking Data**. In addition to the overall log shipping and backup plan, the BizTalk Tracking (BizTalkDTADb) database has its own archive and purge regimes; for more information, see [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md). The speed at which data can be archived and purged from the BizTalk Tracking database is especially important since archiving and purging of the BizTalk Tracking database is typically a bottleneck when tracking is in use.  
  
- **System Queries**. Using APIs or the BizTalk Server Administration Console UI to run various types of queries against the system will affect sustainable performance.  
  
- **MessageBox Maintenance**. There are a number of SQL jobs that are part of the core functionality of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that maintain the MessageBox database by cleaning up messages and instances that have finished processing. As part of the core engine, the speed at which these jobs can complete is a key factor in gauging sustainability. For more information about these jobs and their role, see [Maintaining BizTalk Server1](../core/maintaining-biztalk-server1.md).  
  
- **Solution Deployment Activities**. When deploying, binding, and starting new applications or new versions of existing applications, additional load is placed on BizTalk such as the creation of new subscriptions on the MessageBox database(s). After applications are deployed, the messages being processed will compete for resources and thereby affect the performance of the existing applications.  
  
  For each of these areas, you need to ask: What is your recommendation to minimize the impact of these activities? For example, should they plan to run them at 3am?  
  
## Considering Planned and Unplanned Outages  
 The effects that outages have on the system performance will vary depending on the system experiencing the outage, however the most common consequences are:  
  
- **Floodgate Events**. When systems are down for some length of time, messages can build up and then arrive all at once for processing once the systems are functional again.  For example, if an application running on BizTalk receives messages via MSMQ, and that application is down for some time, messages build up in the queues waiting to be picked up. When the application is started up again, it is as if a large number of messages arrived "all at once."  
  
- **Message Backlog**. When systems to which messages are sent are down, there is typically a retry cycle that is employed that uses additional resources. After the retry cycle is exhausted, then messages are typically suspended. Then the downed systems come back on line, a type of floodgate event occurs where large numbers of messages can now be resumed and/or successfully sent.  
  
  Certainly any planned outages such as regularly scheduled maintenance must be taken into consideration when designing and certifying a system. It is also recommended that an analysis of unplanned outages and their effects be considered.  
  
  Identifying the types of outages that can occur, ranking them by estimated risk level (that is, probability times severity), and estimating the duration and effect (for example, floodgate events, suspended message volume, backlog, etc.) of the higher risk outages will indicate a desired system capability should the outages take place. Any store-and-forward, messaging-based asynchronous system, such as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], should be designed will processing "headroom" sufficient to cope with planned and unplanned outages.  
  
## See Also  
 [Engine Persistence and Durability](../core/engine-persistence-and-durability.md)   
 [Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md)   
 [Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Scaling Your Solutions](../core/scaling-your-solutions.md)   
 [Identifying Performance Bottlenecks](../core/identifying-performance-bottlenecks.md)   
 [Engine Performance and Capacity](../core/engine-performance-and-capacity.md)