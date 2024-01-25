---
description: "Learn more about: Asynchronous Business Event Tracking"
title: "Asynchronous Business Event Tracking"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Asynchronous Business Event Tracking
Asynchronous (using `BufferedEventStream`) - This model offers significant performance improvements. This uses a similar API to the synchronous model, using only a different constructor. Instead of pushing the data into the primary import database, BufferedEventStream accumulates the event data in memory in binary form, and then inserts it as a single table record into an interim database (MessageBox). The Event Bus service reads the data queued in the MessageBox database by BizTalk and imports it into the primary import database.  
  
 To configure BAM for asynchronous operation, the Event Bus Service and the calling application (e.g. Orchestration Host) should run on different computers. This allows the calling application to get rid of the event data immediately to be processed using the CPU on a different computer.  
  
 This BAM topology is also transaction-consistent. You will never get BAM data for transactions that rolled back in the calling application, because the Event Bus Service only reads the committed data from the MessageBox database. The BAM data for the transactions that were committed will show up for query and aggregation with small latency.  
  
 If errors occur, the Event Bus Service will retry a few times, use timeouts, crash recovery logic, and so on. If however the data is in an invalid format, it ends up in special tables. An event occurs in the event log to indicate this condition. This additional failure point increases the difficulty of managing the system.  
  
 Using the asynchronous approach from code is usually as simple as replacing the DirectEventStream with BufferedEventStream, and passing the connection string to the Message Box in the constructor, instead of the one for BAM Primary Import.  
  
 Use the following guidelines regarding asynchronous business event tracking in your code:  
  
-   Always use continuation when the Activity spans multiple applications and you send the data asynchronously to BAM, even if you propagate the ActivityID to all components. In this case, use a different ActivityID in each application by prefixing it with a unique string (e.g. Application Name). This is necessary because the data from different applications might arrive to BAM in random order, and BAM has to manage the out-of-order events to ensure correct Query and Aggregation results.  
  
-   The usual methods of event monitoring (e.g. COM+ Loosely Coupled Events or WMI Events) are not applicable for BAM because the event data is independent of the transaction. For example, it may look like you received 10 purchase orders for a total of $10,000 while there was only one incoming purchase order for $1000, but the attempt to save it to the database failed 10 times.  
  
## See Also  

 [Synchronous Business Event Tracking](../core/synchronous-business-event-tracking.md)
