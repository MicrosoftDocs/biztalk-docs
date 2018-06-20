---
title: "Understanding DTA Tracking Performance Behavior | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1a70951-bfed-435c-97f4-0b28a8e4e4dc
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Understanding DTA Tracking Performance Behavior
The primary factors that determine maximum sustainable throughput (MST) for DTA tracking are:  
  
- The desired message throughput, that is, messages received per unit time, for the system.  
  
- How much data is being tracked for each message.  
  
- How long the data is to live in the BizTalkDTADb database before being purged, that is, the data retention window.  
  
- Whether or not the BizTalkDTADb data is archived as well as purged. Archiving is optional but purging must be performed periodically.  
  
  There is one thing that all of these factors have in common: the speed at which the DTA can accept and process (archive and purge) data.  
  
## How the BizTalkDTADb Insert and Processing Speed Affects Your System  
 Now, let’s walk through the tracking data pathway that is described in [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md), and evaluate the affect of BizTalkDTADb insert and processing speed on the various components of the system.  
  
 Starting with the trackingdata and spool tables, we can imagine that, if the processes that move data from these tables to the BizTalkDTADb database are not able to insert data into the BizTalkDTADb database at least as fast as the runtime is inserting into the trackingdata and spool tables, then the spool and trackingdata tables will start to build up a backlog. This isn’t necessarily a bad thing in the short term as long as you know the message throughput will be reduced to allow the backlog to eventually drain. However, as long as the data is still sitting in the spool or trackingdata tables, it will not be available in the BizTalkDTADb database for querying by tracking queries on the Group Hub page or any other tool.  Thus it will not be useful for problem resolution. Therefore any expected backlog periods must be short enough that the tracked information is still available in a timely fashion should a problem arise that needs to be investigated using BizTalkDTADb data.  
  
 From testing, we know that it isn’t the processes that move tracking data to the BizTalkDTADb database (that is, TDDS and TrackedMessages_Copy_BizTalkMsgBoxDb) that are the determining factor if a backlog builds up, but the speed of the BizTalkDTADb database in accepting the input. Typically, it is the data file of the BizTalkDTADb database that is I/O bound. That is, it is the speed of the drive that the BizTalkDTADb database data file resides on that will determine the speed of the DTA overall.  
  
## How the Amount of Data in BizTalkDTADb Affects I/O Speed  
 Another key factor related to the I/O speed is the amount of data in the BizTalkDTADb database: as the amount of tracked data in the BizTalkDTADb database increases, the input and processing speed of the BizTalkDTADb database decreases since there is simply more data to sort through as new data is inserted, and this affects the amount of I/O required for each insert.  
  
 This is where archiving and purging enter the picture since it is these processes that keep the BizTalkDTADb database from growing too large to keep up. The basic idea is to make sure that the BizTalkDTADb database size is kept below the level at which things begin to backup in the spool and trackingdata tables. However, the purge and archive processes implemented in the DTA Purge and Archive (BizTalkDTADb) SQL Job also require resources (CPU, Memory, and especially I/O) from the BizTalkDTADb database server, which must be taken into account when measuring MST with tracking.  
  
## See Also  
 [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Test Scenarios for Measuring MST of DTA Tracking](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md)   
 [Tips and Tricks for Finding MST of DTA Tracking](../core/tips-and-tricks-for-finding-mst-of-dta-tracking.md)   
 [Tracking Database Sizing Guidelines](../core/tracking-database-sizing-guidelines.md)