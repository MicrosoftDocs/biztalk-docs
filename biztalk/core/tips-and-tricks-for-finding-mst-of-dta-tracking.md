---
title: "Tips and Tricks for Finding MST of DTA Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d72e4ac-d952-4cff-9a65-491e20945d40
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tips and Tricks for Finding MST of DTA Tracking
By definition, MST is a benchmark to reproducibly measure system performance using a constant load. Following are situations where knowing the MST is particularly useful.  
  
1. **When you require the lowest latency from the system**. Exceeding MST results in backlog in the system, which introduces increased latency for messages. Even if the backlog is only temporary, backlog has an immediate and deleterious effect on latency. So, knowing your systems MST will tell you the absolute maximum throughput you should expect to achieve before the latency of individual message processing increases dramatically (for example, from seconds to minutes depending on your configuration).  
  
2. **When comparing to other systems**. For example, if you want to validate that you are achieving the expected MST compared to another system (for example, the scenario in this topic, a case study, or another system in your environment); measuring MST using a steady input offers a reproducible, unambiguous standard for comparison.  
  
   Needless to say, however, it can be time consuming to measure MST. Therefore, before you embark on a lengthy exercise to measure it, you should evaluate the benefits. Most production systems will not experience a steady input such as that measured by MST, but rather a load that changes over time. It is this load profile that must ultimately be tested to certify a system prior to production. Fortunately, you can use the same technique that is used to measure MST to evaluate the sustainability of your production load profile. Simply run your load profile long enough to include one or more BizTalkDTADb database data retention windows and observe the key performance indicators (KPI).  
  
   It is important to start your test runs, whether MST or load profiles, with an empty BizTalkDTADb database. The data that is stored in the BizTalkDTADb database is time sensitive and if it is not re-acquired from scratch for each test run, it can skew your results. Depending on your data retention window, this can significantly increase the time it takes to find MST. To mitigate this, adjusting load "on the fly" during test runs can be useful in more quickly zeroing in on MST.  
  
   For example, if you find that you have passed your first retention window time and the KPIs indicate you have headroom for higher throughput left (for example, disk idle time is still above zero), you can incrementally increase your load and observe the effect. After you have refined your MST estimate in this way, however, it is important that you perform a test run starting with an empty BizTalkDTADb database to validate your estimate.  
  
## Recommendations  
 The tracking system architecture in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is capable of tracking a wide variety of information and must be managed and monitored carefully. The factors that will most affect the performance of your system, as indicated by MST, are as follows:  
  
- The desired throughput for the system.  
  
- The volume of information tracked for each message and service instance in the system. This will determine how quickly the size of the BizTalkDTADb database increases, and ultimately how often the BizTalkDTADb database must be purged to avoid falling behind.  
  
- How long you wish to retain data in the BizTalkDTADb database, that is, the data retention window. The longer the window, the larger the BizTalkDTADb database will grow, affecting throughput.  
  
- Whether you archive BizTalkDTADb database data as well as purge, or just purge to maintain BizTalkDTADb database size.  
  
  The process of finding the maximum sustainable throughput for tracking in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] involves three key performance indicators:  
  
- Physical Disk Idle Time for the DTAdb data file disk subsystem.  
  
- Spool depth  
  
- BizTalkDTADbData depth  
  
  Find either your systems’ MST or validate your production profile throughput by monitoring these three key performance indicators looking for:  
  
- Stable spool and trackingdata table depth.  
  
- BizTalkDTADb database data file disk physical idle time near, but not continuously "pegged" at, zero.  
  
  Using the DTA tracking features has an associated performance impact.  Default tracking may track more than is needed once a solution is in production, but can make development and initial testing and debugging easier by providing ample problem resolution information. Therefore, we recommend that default tracking be left on during development and initial testing. Once a solution deployed on BizTalk is stable and ready for production certification, including performance testing, it is recommended that you carefully examine the amount of information that needs to be tracked in production, and the length of time it needs to be kept in the BizTalkDTADb database and adjust accordingly.  
  
  For example, if message bodies do not need to be tracked for either non-repudiation or problem resolution purposes, then do not turn on message body tracking. To illustrate this point, in the example scenario described in [Test Scenarios for Measuring MST of DTA Tracking](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md), when the message body tracking component of the tracking configuration was eliminated, the MST was doubled to 40 messages/second.  
  
  Also, keep in mind that even when problems do occur, in many (but by no means all) cases, messages are suspended in the MessageBox database and can be retrieved and inspected without needing to track message bodies.  
  
  Focus on the sustainability of the load you place on the system:  
  
- Can your system sustain the production load profile indefinitely even with normal maintenance activities?  
  
- What if something happens that causes the system to sustain a backlog, such as a planned or unplanned BizTalkDTADb database outage?  
  
  It is a good idea to set goals based on worst case scenarios and test to those goals. For example, if you know that there is a periodic planned maintenance cycle that will take the BizTalkDTADb database off line, emulate this outage during a test run to evaluate the ability of the system to recover from the resulting backlog.  
  
## See Also  
 [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Understanding DTA Tracking Performance Behavior](../core/understanding-dta-tracking-performance-behavior.md)   
 [Test Scenarios for Measuring MST of DTA Tracking](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md)   
 [Tracking Database Sizing Guidelines](../core/tracking-database-sizing-guidelines.md)