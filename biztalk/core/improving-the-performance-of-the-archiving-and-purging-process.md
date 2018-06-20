---
title: "Improving the Performance of the Archiving and Purging Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "archiving [Tracking database], system performance"
  - "DTA Purge and Archive job, performance"
  - "purging, limitations"
  - "performance, archiving"
  - "performance, purging"
  - "purging, system performance"
ms.assetid: d65da58d-65e0-4f6c-8b15-5d4448049b42
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Improving the Performance of the Archiving and Purging Process
The amount of data stored in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases can grow very quickly depending on how you have designed your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] scenario, depending on the number and size of messages processed by your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] scenario, and depending on how you have configured tracking. By maintaining your database size at a healthy level, processing is more efficient and the amount of data in your system is normalized at any given time. This provides efficient and consistent performance. By automating this process you free yourself of the burden of manually maintaining your databases.  
  
## Configuring a healthy environment  
 Your strategy in maintaining a healthy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment is heavily dependent on your particular scenario and the hardware it is running on. The key things to monitor are the rate of growth and the size of your BizTalk Tracking (BizTalkDTADb) database. A few tables of the tracking database account for bulk of the database size and hence the performance impact on runtime.  
  
 The same scenario can be configured to produce vastly different amount of tracking data based on how many tracking points are present, how many different messages are used, size of the messages and the level of message body tracking used. Following are some important factors to monitor:  
  
- Number of tracking points - such as pipelines, orchestrations, and ports  
  
- Number of message properties tracked  
  
- Number of messages per incoming message  
  
- Message size  
  
- Traffic rate (average and peak)  
  
- Message body tracking configuration  
  
  When considering automatic archiving and purging of data consider how much live data you need to keep in your tracking database. You need to tune the DTA Purge and Archive job parameters as appropriate for your environment so that the targeted amount of live data can be supported by the purging performance without degradation.  
  
  The DTA Purge and Archive job can purge a certain amount of data within a given time interval. The capacity of the job depends on the scenarios running, the current database size, and the hardware. In order to have a stable environment, you must have a balance between the incoming tracking data generation and purging. In your test environment, you can find the balance by varying the live window of data and the frequency of the purging job. In a balanced state, your system will deliver sustainable throughput. Your goal is to have enough of a buffer before the BizTalk Tracking database table size causes sustained, significant performance issues.  
  
## Performance limitations  
 Purging performance will not scale for all scenarios. For any scenario, it is possible to generate increasing amounts of tracking data. When tracking data is purged at a consistently slower rate, there is a buildup of the tracking database size, which worsens the purging performance further.  
  
 Under unsustainable load conditions, the copying of message bodies may also become slower and there may become a backlog in the MessageBox database. Under extreme conditions, the daily message body copying and tracking may lead to archives where the message body is not available even though it contains related instance information. Typically, periods of high loads alternate with periods of low load and enable the job to catch up during periods of low load.  
  
 Archiving and purging the BizTalk Tracking database should considerably reduce the possibility of unsustainable load conditions because of the continuous pruning of the database and the compaction of stored tracking data. These processes greatly reduce the need for manual intervention.  
  
## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)