---
title: "Monitor the health and performance using built-in tools | Microsoft Docs"
description: Availability, health, and performance monitoring in BizTalk Server, and monitor SQL Agent jobs
ms.custom: ""
ms.date: "01/14/2016"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96e244dc-b826-4a9f-a4e1-6dabc41eb144
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitoring BizTalk Server
Monitoring your BizTalk Server applications and infrastructure on a regular basis and resolving any issues that you find helps to keep your BizTalk Server applications accessible to your users. The goal of monitoring is to minimize the amount of time that an exception goes undetected and, therefore, unresolved. Additionally, you can use monitoring to help detect situations that might cause an exception.  
  
 When monitoring BizTalk Server, you should look for any unexpected or anomalous behavior. Monitoring can be either a manual or automatic process. You can monitor use the health of your BizTalk Server infrastructure using the BizTalk Server Administration Console. You can use the BizTalk Server Administration Console to monitor the health of your BizTalk Server applications and perform root-cause analysis to identify the underlying cause of any problems. . When monitoring BizTalk Server, keep these points in mind:  
  
- Your infrastructure could be healthy, but your applications might not be (for example, they are receiving invalid messages and are unable to process them).  
  
- Your infrastructure could be unhealthy, but your applications might be running fine (for example, if a server is down, but there are enough servers assigned to the host to take over the load).  
  
- An infrastructure problem could surface as an application problem (for example, messages are not being processed fast enough because a server is down).  
  
  Monitoring your BizTalk Server and Applications falls into three main categories:  
  
- Availability monitoring  
  
- Health monitoring  
  
- Performance monitoring  
  
## Availability Monitoring  
 Availability monitoring answers the question "Is the inavailability of a system or application resource preventing your BizTalk Server applications from running optimally?" These issues are almost exclusively system-level, such as availability of services and connections. For example, if an adapter is failing because the Enterprise Single Sign-On service is stopped, this is an availability issue. If one of the servers assigned to a host has failed and your application is falling behind on processing messages, you have an availability issue. Likewise, if an application is stopped and is unable to process messages, you have an availability issue. The following table shows availability monitoring tools.  
  
|Tool|Task|  
|----------|----------|  
|BizTalk Server Administration Console|You should look at the Group Hub page in the BizTalk Server Administration Console to see if applications or their components (ports/orchestrations) are stopped.|  
|Event Viewer|Look for adapter connection issues, stopped services, and so on.|  
  
## Health Monitoring  
 Health monitoring helps you answer the question, "Are any of my applications or resources in bad health?" For example, are any of my applications or their constituent artifacts currently experiencing exception conditions? Or, are messages suspended because of invalid data in the message payload? The following table shows health-monitoring tools.  
  
|Tool|Task|  
|----------|----------|  
|BizTalk Health Monitor tool (BHM)|An MMC snap-in for users to monitor the health of BizTalk Server environments, detect critical and non-critical issues, and execute maintenance tasks.  [Download BizTalk Health Monitor](https://www.microsoft.com/download/details.aspx?id=43716).|  
|BizTalk Server Administration Console|You will use the Group Hub page and query pages in the BizTalk Server Administration Console to identify application health problems and analyze their cause(s).|  
|Event Viewer|Detect problems that occur during the processing of messages and orchestrations.|  
  
## Performance Monitoring  
 Performance monitoring answers the question, "How efficiently is the system performing its work?" This kind of monitoring focuses primarily on the load on physical resources like databases and disks. For example, if the CPU utilization is consistently at 90 to 100 percent and a backlog of messages is forming, this is a performance issue at the computer level. The following table shows performance-monitoring tools.  
  
|Tool|Task|  
|----------|----------|  
|SQL Query Analyzer|Monitor database size and content to diagnose system problems.|  
|BizTalk Server Administration Console|The Group Hub Page shows key performance metrics such as the number of service instances currently active, dehydrated, ready to run, scheduled, suspended, etc. in your BizTalk Server applications.|  
|Business Activity Monitoring (BAM)|You can specify specific stages in your business process for which you want to track key performance indicators pertinent to your business application.|  
  
## BizTalk Server Monitoring  
 You can run the **Monitor BizTalk Server** SQL Agent job to identify any known issues in Management, Message Box, or DTA databases. The job is created when you configure a BizTalk group in BizTalk Server Administration console or upgrade BizTalk from the previous version.  
  
 The Monitor BizTalk Server job scans for the following issues in Management, Message Box, and DTA databases:  
  
> [!NOTE]
>  The Monitor BizTalk Server job only scans for issues. It does not fix the issues found.  
  
- Messages without any references  
  
- Messages without reference counts  
  
- Messages with reference count less than 0  
  
- Message references without spool rows  
  
- Message references without instances  
  
- Instance state without instances  
  
- Instance subscriptions without corresponding instances  
  
- Orphaned DTA service instances  
  
- Orphaned DTA service instance exceptions  
  
- TDDS is not running on any host instance when global tracking option is enabled.  
  
  The Monitor BizTalk Server job is configured and automated to run once in a week. Since the job is computationally intensive, we recommended you to schedule it during downtime/low traffic.  
  
  The job fails if it encounters any issues; error string contains the number of issues found. Else, it runs successfully. You can see the details in the job history. If you run the job with Administrator privileges, error string will be logged to Event Viewer also (along with the job history).  
  
## Troubleshooting  
 Once you are aware of a health problem with your BizTalk Server applications (not infrastructure), you can use the Group Hub page and Query pages in the BizTalk Server Administration Console to analyze the problem. The BizTalk Server Administration Console provides an integrated configuration, deployment and troubleshooting experience, and you can fix configuration and deployment related problems within the Administration Console after you have pinpointed them. Typically, most application problems are due to messages not getting through as expected (this can manifest as suspended service instances, or retrying ports, or dehydrated instances that have not been reactivated, etc.)  
  
 You can use the Group Hub page and Query pages to group your service instances (whatever state they are in: running, suspended, dehydrated, etc) by Application, Error type, Service Type, Host, etc, to isolate the different errors, investigate them one by one, and fix them. You can also monitor tracking data from within the BizTalk Server Administration Console, to investigate the history of a message flow, or the history of execution of an orchestration or rule set. This tracking data contains historical data about your BizTalk Server applications.  
  
 If you have enabled tracking in the BizTalk Administration Console, you can use tracking to locate message flow and service instances using a query. This is useful when you want to locate a message and know only, for example, the message type (schema), a property and its value (for example, customer name), etc.  
  
 The following topics discuss monitoring and troubleshooting using the BizTalk Server Administration Console, Group Hub page, and Query pages. This section also discusses tracking, which you can use as an aid in troubleshooting and root-cause analysis.  
  
## More good stuff  
  
-   [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md)  
  
-   [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)  
  
-   [Monitoring EDI and AS2 Solutions](../core/monitoring-edi-and-as2-solutions.md)  
  
-   [Tracking Dependencies Between Artifacts in a BizTalk Server Application](../core/tracking-dependencies-between-artifacts-in-a-biztalk-server-application.md)

- [Performance Counters](performance-counters.md)