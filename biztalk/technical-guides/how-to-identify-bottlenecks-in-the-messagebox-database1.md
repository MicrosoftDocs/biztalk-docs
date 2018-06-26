---
title: "How to Identify Bottlenecks in the MessageBox Database1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a039164-5ca6-4cbc-b307-c5d4ae800689
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Identify Bottlenecks in the MessageBox Database
To identify bottlenecks in the MessageBox database, first ensure that the SQL-Server-Agent Service is started. Change the Service startup state from Manual to Auto so that if the server is restarted, the service will automatically restart.  
  
 By default, the BizTalk service will throttle if the Spool, TrackingData, or ApplicationQ tables grow. These tables are pruned by SQL-Agent jobs, which, if not running will cause the Spool to grow causing throttling to start and protect the database from additional pressure. Check the status of the following performance counters:  
  
- BizTalk:Message Agent (Host Name) Message Delivery Throttling State  
  
- BizTalk:Message Agent (Host Name) Message Publishing Throttling State  
  
  A value of “0” indicates no throttling is occurring. A value of “6” indicates the system is throttling due to database growth. For information about how to interpret the values of these counters, see [What is Host Throttling?](http://go.microsoft.com/fwlink/?LinkID=154694) (http://go.microsoft.com/fwlink/?LinkID=154694) and [Host Throttling Performance Counters](http://go.microsoft.com/fwlink/?LinkID=155285) (http://go.microsoft.com/fwlink/?LinkID=155285) in the BizTalk Server 2010 documentation.  
  
## Spool table growth  
 The Spool can start growing for multiple reasons. One reason for Spool growth is if the Application Queues are growing. They could grow due to reasons such as downstream bottlenecks and/or resource contention.  
  
 If the Application Queues are small and the Spool is still large, verify that the purge jobs are keeping up. Ensure that the SQL-Agent Service is running and then verify that the following jobs are successfully completing:  
  
- MessageBox_Message_Cleanup_BizTalkMessageBoxDb  
  
- MessageBox_Parts_Cleanup_BizTalkMessageBoxDb  
  
  If the MessageZeroSum table is large, it indicates that the messages have been processed. This means that DeQueue has successfully completed and deleted data from the Application Queue tables and the rows have been flagged for deletion. However, the purge jobs are unable to keep up with deleting the data. This can happen if the computer running SQL Server is experiencing severe CPU contention, affecting the ability of the purge jobs to keep up due to CPU starvation.  
  
## Application queue table growth  
 Application Queues host in-flight transition data that, once processed, are cleaned up by DeQueue.  
  
 After these messages are processed, the Spool table (holding references to these rows) can be cleaned.  
  
 For example, the RxHostQ publishes data to the orchestration PxHostQ. This queue publishes data to the sending TxHostQ each referencing a row in the Spool table. After the messages for a particular HostQ have successfully processed through the system, these rows are deleted by DeQueue. After these rows are deleted, the Spool (which is no longer referenced by these rows) can then be cleaned by the purge jobs.  
  
 Application Queue growth indicates that the host instances responsible for draining the Application Queue are unable to keep up with the incoming rate.  
  
 For example, the orchestration application queue (PxHostQ) may grow because the server responsible for processing orchestrations is CPU bound and unable to process any faster. However, if the receiving server is fast it may publish faster than what the orchestration server can process leading to the Application Queue growth.  
  
 Another reason for orchestration queue growth could be due to memory contention. When many long running orchestration instances are concurrently instantiated in memory, memory bloat indirectly causes throttling to shrink the thread pool until memory pressure is relieved.  
  
 A reason why the send application queue may grow is if the downstream system is unable to receive messages (outgoing from BizTalk Server) fast enough. Thus the messages will continue to reside within the BizTalk system causing Application Queue growth. This can cause throttling to start and reduce the receiving rate impacting the overall throughput of the system.  
  
## TrackingData table growth  
 The TrackingData table in the MessageBox database is a transition table into which interceptors write tracking data for both Health and Activity (HAT) and Business Activity Monitoring (BAM) tracking. If tracking is disabled, this table should be empty. By default, HAT-tracking is enabled for the pipelines and orchestrations In/Out events.  
  
 If Message Body Tracking is enabled, ensure that the MessageBox database server (that is, the host with "allow host tracking") is running. Ensuring that the host with "allow host tracking" is running will reduce the chance of a bottleneck occurring as the host moves data from TrackingData table in the MessageBox database to the BizTalk Tracking database tables.  
  
 It is possible to track custom events by enabling custom HAT-tracking, for example, on promoted properties and message body tracking. In addition to HAT-tracking data, BAM data is also written to the TrackingData table. The Tracking Data Decode Service (TDDS, which runs on the host instance on which tracking is enabled) is responsible for moving this data from the MessageBox database to the BizTalk Tracking and BAM Primary Import databases. Then after the data is successfully moved, TDDS deletes this data. Message body tracking data is moved separately by a SQL-Agent job TrackedMessages_Copy_BizTalkMsgBoxDb.  
  
 If TDDS is unable to keep up with the rate at which the interceptors are writing data to the TrackingData table, this table will grow, causing throttling to start. This impacts sustainable throughput. To lessen this problem, ensure at least one host is running with tracking enabled.  
  
 If the data still builds up, ensure the BizTalk Tracking database is not growing out of control. Also, ensure the archiving and purging job is running and is able to keep up with the rate at which data is arriving.  
  
> [!NOTE]  
>  By default, the purge job is unable to delete data from the BizTalk Tracking database tables until this data has been archived. If you do not need to archive the tracking data, you can modify the job to purge the BizTalk Tracking database without archiving by following the steps at [How to Purge Data from the BizTalk Tracking Database](http://go.microsoft.com/fwlink/?LinkID=153817) (http://go.microsoft.com/fwlink/?LinkID=153817).  
  
## See Also  
 [Bottlenecks in the Database Tier](../technical-guides/bottlenecks-in-the-database-tier.md)