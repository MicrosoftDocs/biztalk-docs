---
title: "How to Identify Bottlenecks in the MessageBox Database2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10b2eb1e-541c-457d-9735-ac6fb069b209
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Identify Bottlenecks in the MessageBox Database
To identify bottlenecks in the MessageBox database, first ensure that the SQL-Server-Agent Service is started. Change the Service startup state from Manual to Auto so that even if the server is restarted, the service will automatically restart.  
  
 By default the BizTalk service will throttle if the Spool, TrackingData or ApplicationQ tables grow. These tables are pruned by SQL-Agent jobs, which, if not running will cause the Spool to grow causing throttling to kick in protecting the database from additional pressure. Check the status of the following performance counters:  
  
- BizTalk:Message Agent (Host Name) Message Delivery Throttling State  
  
- BizTalk:Message Agent (Host Name) Message Publishing Throttling State  
  
  A value of 0 indicates no throttling is occurring. A value of 6 is indicative the system is throttling due to database growth. Please refer to the documentation on how to interpret other values of these counters.  
  
## Spool Table Growth  
 The Spool can start growing for multiple reasons. One reason for Spool growth is if the application queues are growing. They could grow due to various reasons like downstream bottlenecks and/or resource contention.  
  
 If the application queues are small and the Spool is still large, verify that the purge jobs are keeping up. Ensure that the SQL-Agent Service is running and then verify that the following jobs are successfully completing:  
  
- MessageBox_Message_Cleanup_BizTalkMessageBoxDb  
  
- MessageBox_Parts_Cleanup_BizTalkMessageBoxDb  
  
  If the MessageZeroSum table is large it indicates that the messages have been processed (DeQueue has successfully completed and deleted data from the Application Queue tables) and the rows have been flagged for deletion. However, the purge jobs are unable to keep up with deleting the data. One reason for this is if the SQL-Server machine is experiencing severe CPU contention, impacting the ability of the purge jobs to keep up due to CPU starvation.  
  
## Application Queue Table Growth  
 Application queues host in-flight transition data that, once processed, are cleaned up by DeQueue.  
  
 After these messages are processed the Spool (holding references to these rows) can be cleaned.  
  
 For example, the RxHostQ publishes data to the orchestration PxHostQ which in turn publishes data to the sending TxHostQ each referencing a row in the Spool table. After the messages for a particular HostQ have successfully processed through the system these rows are deleted by DeQueue. After these rows are deleted, the Spool (which is no longer referenced by these rows) can then be cleaned by the purge jobs.  
  
 Application Queue growth indicates that the Host Instances responsible for draining the Application Queue are unable to keep up with the incoming rate, that is, the rate at which messages are being published to the particular application queue.  
  
 For example, the orchestration application queue (PxHostQ) may grow because the server responsible for processing orchestrations is CPU bound and unable to process any faster. However, if the receiving server is fast it may publish faster than what the orchestration server can process leading to the application queue growth.  
  
 Another reason for orchestration queue growth could be due to memory contention whereby numerous long running orchestration instances are all concurrently instantiated in memory, causing memory bloat indirectly causing throttling to shrink the thread pool until memory pressure is relieved. One reason why the send application queue may grow is if the downstream system is unable to receive (outgoing from BizTalk) messages fast enough. Thus the messages will continue to reside within the BizTalk system causing Application queue growth which will ultimately cause throttling to kick in reducing the receiving rate impacting the overall throughput of the system.  
  
## TrackingData Table Growth  
 The TrackingData table in the MessageBox database is a transition table into which interceptors write tracking data for both message and service instance tracking and BAM tracking. If tracking is disabled, this table should be empty. By default message and service instance tracking is enabled for the pipelines and orchestrations In/Out events.  
  
 If Message Body Tracking is enabled, ensure that the MessageBox server (that is, the host with "allow host tracking") is running. It will reduce a bottleneck as it moves data from TrackingData table in the MessageBox database to the BizTalkDTADb tables.  
  
 It is possible to track custom events by enabling custom message and service instance  tracking, for example, on promoted properties and message body tracking. In addition to tracking data, BAM data is also written to this table. It is the responsibility of TDDS (the host on which tracking is enabled) to move this data from the MessageBox database to the BizTalkDTADb and BAMPrimaryImport databases, and then once successfully moved, delete this data. Message body tracking data is moved separately by a SQL-Agent job TrackedMessages_Copy_BizTalkMsgBoxDb.  
  
 If TDDS is unable to keep up with the rate at which the interceptors are writing data to the TrackingData table, this table will grow, causing throttling to kick in, ultimately impacting sustainable throughput. To alleviate this problem, ensure that at least 1 host is running with tracking enabled.  
  
 If the data still builds up, verify the BizTalkDTADb database to ensure that the database is not growing out of control. Ensure that the archiving and purging job is running and is able to keep up with the rate at which data is arriving.  
  
> [!NOTE]
>  The purge job is unable to delete data from the BizTalkDTADb tables until this data has been archived.  
  
 Verify that the TrackingData table is not growing. Ensure that at least 1 host instance that is running has tracking enabled (TDDS). If the BizTalkDTADb database has grown too large, it can have a negative impact on the ability of TDDS to move data from the MessageBox database to the BizTalkDTADb database.  
  
 Growth in the TrackingData table can cause throttling to kick in, impacting sustainable runtime throughput.