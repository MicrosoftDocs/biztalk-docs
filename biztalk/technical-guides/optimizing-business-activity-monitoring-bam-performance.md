---
title: "Optimizing Business Activity Monitoring (BAM) Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9ed29b2-0be6-4a37-be68-9476832fd49f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Optimizing Business Activity Monitoring (BAM) Performance
This topic describes Business Activity Monitoring (BAM) performance factors.  
  
## BAM disk usage configuration  
 BAM incurs significant overhead when a BizTalk system is under load because of the significant amount of data that is persisted to the BAM database. Therefore, judicious use of disk I/O techniques for the BAM database is critically important.  
  
## BAM EventStream APIs  
 Four types of EventStreams are available for use in a BizTalk BAM scenario:  
  
- DirectEventStream (DES)  
  
- BufferedEventStream (BES)  
  
- OrchestrationEventStream (OES)  
  
- MessageEventStream (MES)  
  
  You should choose one of these APIs based on the following factors:  
  
- If your concern is latency, choose DES, where data is persisted synchronously to the BAM Primary Import database.  
  
- If your concern is performance and throughput of event insertion, choose an asynchronous API (BES, OES or MES).  
  
- If you are writing an application that runs on a computer that does not have BizTalk Server installed, use DES and BES; these APIs can be used in non-BizTalk applications.  
  
  > [!NOTE]  
  >  There are scenarios in which you may want to mix EventStream types. For example, for pipeline processing, you may want to capture the particular data in BAM regardless of whether the pipeline is rolling back its transaction. In particular, you may want capture data about how many messages failed or how many retries occurred during pipeline processing. To capture the data in this situation you should use BES.  
  
- If your application runs on a computer on which BizTalk Server is installed, use MES and OES. (These APIs are available only from BizTalk applications.)  
  
  > [!NOTE]  
  >  OES is the equivalent of MES but for BizTalk orchestrations.  
  
- If you want BAM event persistence to be in sync with pipeline transaction, you should use a Messaging Event Stream (MES).  
  
  All the asynchronous EventStreams (BES, MES, and OES) persist data first to the BizTalk MessageBox database. Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).  
  
  For more information about the BAM EventStream APIs, see [EventStream Classes](http://go.microsoft.com/fwlink/?LinkId=158046) (http://go.microsoft.com/fwlink/?LinkId=158046) in the BizTalk Server documentation.  
  
## BAM performance counters  
 For a detailed list of the performance counters for BAM, see [BAM Performance Counters](http://go.microsoft.com/fwlink/?LinkId=158048) (http://go.microsoft.com/fwlink/?LinkId=158048) in the BizTalk Server documentation.  
  
## See Also  
 [Optimizing BizTalk Server Performance](../technical-guides/optimizing-biztalk-server-performance.md)