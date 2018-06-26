---
title: "EventStream Classes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3e7a6b3-69cc-4312-9074-acccd1175d37
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EventStream Classes
The EventStream APIs for BAM reside in the Microsoft.BizTalk.BAM.EventObservation namespace. To code against the APIs, you must install the following DLLs on your development computer:  
  
- Microsoft.BizTalk.BAM.EventObservation.dll  
  
- Microsoft.Biztalk.BAM.Xlangs.dll: This DLL is required when coding for Orchestration event streams.  
  
- Microsoft.BizTalk.Pipeline.dll: This DLL required when using coding pipeline contexts for Messaging event streams.  
  
  Add the DLL to your project reference and include the namespace in your code with the following using statement:  
  
```  
using Microsoft.BizTalk.Bam.EventObservation;  
```  
  
 **Classes**  
  
|Name|Description|  
|----------|-----------------|  
|DirectEventStream (DES)|Synchronous, no latency|  
|BufferedEventStream (BES)|Asynchronous, high throughput, some latency|  
|OrchestrationEventStream (OES)|Asynchronous, participates in BizTalk orchestration transactions|  
|IPipelineContext Interface|Asynchronous, participates in BizTalk Server pipeline transactions. Used to create Messaging Event Streams (MES).|  
  
 You should choose an API based on the following factors:  
  
- If your concern is latency, choose DES, where data is persisted synchronously to the BAM Primary Import database. Except for DES, all other EventStream classes are asynchronous and have some latency. The data is first persisted to MessageBox and subsequently processed by TDDS which moves data into the BAMPrimaryImport database.  
  
- If your concern is performance and throughput of event insertion, choose an asynchronous API.  
  
- If you are writing an application that runs on a computer that does not have BizTalk Server installed, use DES and BES. (In other words, these APIs can be used in non-BizTalk applications.)  
  
- If your application runs on a computer on which BizTalk Server is installed, use MES and OES. (These APIs are available only from BizTalk applications.)  
  
  -   If you want BAM event persistence to be in sync with pipeline transaction, you should use a Messaging Event Stream.  
  
  -   OES is the equivalent of MES but for BizTalk orchestrations.  
  
  There are scenarios in which you may want to mix EventStream types. For example, in a pipeline processing, you may want to capture the particular data in BAM regardless of whether the pipeline is rolling back its transaction. In particular, you may want capture data about how many messages failed or how many retries there were during pipeline processing. To capture the data in this situation you should use BES.  
  
  All the asynchronous EventStreams (BES, MES, and OES) persist data first in the BizTalk MessageBox database. Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).  
  
> [!NOTE]
>  To ensure that EventStream calls do not create a bottleneck from a BizTalk application, we recommend that you use asynchronous APIs.  
  
## In This Section  
  
-   [OrchestrationEventStream](../core/orchestrationeventstream.md)  
  
-   [Messaging Event Streams](../core/messaging-event-streams.md)