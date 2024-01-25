---
description: "Learn more about: Engine Persistence and Durability"
title: "Engine Persistence and Durability"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Engine Persistence and Durability
This section explains how BizTalk Server reliably integrates loosely coupled business processes by persisting process state to disk via SQL Server. By persisting state at appropriate times, leveraging transactions, the system guarantees that no process state is lost even in the event of a hardware or software outage. This is referred to as system durability.  
  
## Loosely Coupled Business Process Management  
 Integrating existing systems to perform a single logical business process requires management of process state outside of the existing systems. Whether the business process is long running or short lived, process state must be maintained independently in order to avoid the explosion of custom communications paths that result from tightly coupling systems together.  
  
 Clearly, the state of a running business process instance must be reliable if the business process is mission critical. To assure that business processes are reliable and durable, BizTalk leverages SQL Server transactions to persist process state and business data to disk in a database known as the MessageBox database. For more information about the MessageBox database, see [The MessageBox Database](../core/the-messagebox-database.md).  
  
 Every message and all but the most trivial business process instances (for example, orchestration instances) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are persisted in the MessageBox database at least once during processing.  
  
## Persistence and Sustainability  
 The fact that BizTalk Server persists all messages and most orchestrations has a direct affect on sustainability as noted in [What Is Sustainable Performance?](../core/what-is-sustainable-performance.md) As messages arrive in the MessageBox database, they are routed to waiting subscribers (for example, orchestrations and send ports) and en-queued, or published, into messagebox SQL tables to wait for subscribers to pick them up and process them. Some of the arriving messages activate new subscriber instances. Other messages arrive and are routed, via correlation, to a waiting instance of an already running subscriber such as a correlated orchestration.  
  
 In order for correlated orchestrations to continue processing, arriving correlated messages must remain un-blocked. To facilitate this, BizTalk does its best to make sure messages (both activating and correlated) continue to be received, even under high load, so that subscribers waiting for correlated messages can finish and make room for more processes to run. This means it is possible to receive messages faster than they can be processed and removed from the MessageBox database, thus building up a message backlog. Being a store-and-forward technology, it is natural for BizTalk to provide this type of buffering, however, it can result in problems if the receive rate is consistently faster than the process rate indefinitely, resulting in a large backlog.  
  
 Every message that is received by, or created within, BizTalk Server is immutable. That is, once it has been received or created, its content cannot be changed. In addition, received messages may have multiple subscribers. Each subscriber of a particular message references the same, single copy of that message. While this approach minimizes storage, a ref-count must be kept for each message and maintenance must be performed periodically to get rid of those messages that have a ref count of 0.  
  
 If a large enough backlog is allowed to build up in the MessageBox database, the maintenance processes for the database (implemented as a set of SQL Jobs for each MessageBox database) will fall behind and, if not given an opportunity to catch up, will eventually cause issues such as running out of disk space. To avoid this situation, BizTalk Server provides a throttling mechanism that slows down the message receive rate when the MessageBox database backlog gets to some user-configurable level. For more information about throttling, see [Optimizing Resource Usage Through Host Throttling](../core/optimizing-resource-usage-through-host-throttling.md).  
  
 Given all of the activities and processes that contribute to sustainability, the primary measure of sustainability over time is that a backlog is not allowed to grow indefinitely. In other words, over time, there must be a balance between the high and low peak throughput levels so that the MessageBox database is able to maintain a constant and manageable average backlog. The primary measure of backlog is the depth of the spool table, which is exposed as a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance counter called BizTalk:Message Box:General Counters:Spool Size. For more information about this performance counter, see [Message Box Performance Counters](../core/message-box-performance-counters.md).  
  
 For more information on how to use the spool size and other counters to determine the maximum throughput a system can sustain, see [Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md).  
  
## Recommendations  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] persists all messages and most orchestrations and can, left un-checked, develop a backlog of messages that can result in issues such as running out of disk space. The primary measure of backlog is the depth of the messagebox spool table, which is exposed as a performance counter called: BizTalk:Message Box:General Counters:Spool Size.  
  
 When thinking about sustainable throughput, the spool size must sustain a stable average over time. That is, the spool cannot continue to grow un-checked indefinitely. In [Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md), this behavior is discussed in more detail and a method of determining the maximum throughput a system can sustain is provided which leverages the spool size and other performance indicators.  
  
## See Also  
 [Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [What Is Sustainable Performance?](../core/what-is-sustainable-performance.md)   
 [Performance Tips and Tricks](../core/performance-tips-and-tricks.md)   
 [Message Box Performance Counters](../core/message-box-performance-counters.md)
