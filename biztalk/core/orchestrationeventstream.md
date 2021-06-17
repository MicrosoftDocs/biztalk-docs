---
description: "Learn more about: OrchestrationEventStream"
title: "OrchestrationEventStream | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7c63610-6344-4b71-8d65-3add7883bc79
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# OrchestrationEventStream
You use the OrchestrationEventStream (OES) API when your application runs on a computer on which BizTalk Server is installed and you are tracking items that are part of BizTalk orchestration transactions.  
  
 The OES API stores tracking data first in the BizTalk MessageBox database. Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).  
  
 The OES API is found in the Microsoft.BizTalk.Bam.EventObservation namespace. To use the API you must add the Microsoft.Biztalk.BAM.Xlangs.dll to your project.  
  
## OES Members  
 The OES API is derived from the [Microsoft.BizTalk.Bam.EventObservation.EventStream](/previous-versions/) class.  
  
 OES implements all of the methods within the EventStream class, but has the  following exception in behaviors:  
  
 **public static void Clear();**  
  
 No operation.  
  
 **public static void Flush();**  
  
 No operation.  
  
## See Also  
 [EventStream Classes](../core/eventstream-classes.md)