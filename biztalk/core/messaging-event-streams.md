---
description: "Learn more about: Messaging Event Streams"
title: "Messaging Event Streams | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2dc56aff-c093-4c79-9cc7-f72079ee927f
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Messaging Event Streams
You use Messaging Event Streams (MES) when your application runs on a computer on which BizTalk Server is installed and you are you are tracking items that are part of BizTalk pipeline transactions. Using MES ensures that your BAM event persistence remains in sync with the BizTalk pipeline transactions.  
  
 Messaging Event Streams are instances of EventStream objects returned by the [Microsoft.BizTalk.Component.Interop.IPipelineContext.GetEventStream](/previous-versions/) method.  
  
 Messaging Event Streams are asynchronous and store tracking data first in the BizTalk MessageBox database. Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).  
  
 IPipelineContext is found in the [Microsoft.BizTalk.Component.Interop](/previous-versions/) namespace. To use the API you must add the Microsoft.BizTalk.Pipeline (in microsoft.biztalk.pipeline.dll) to your project.  
  
## See Also  
 [OrchestrationEventStream](../core/orchestrationeventstream.md)   
 [Microsoft.BizTalk.Bam.EventObservation.EventStream](/previous-versions/)   
 [Microsoft.BizTalk.Component.Interop](/previous-versions/)