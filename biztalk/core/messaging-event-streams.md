---
description: "Learn more about: Messaging Event Streams"
title: "Messaging Event Streams"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Messaging Event Streams
You use Messaging Event Streams (MES) when your application runs on a computer on which BizTalk Server is installed and you are you are tracking items that are part of BizTalk pipeline transactions. Using MES ensures that your BAM event persistence remains in sync with the BizTalk pipeline transactions.  
  
 Messaging Event Streams are instances of EventStream objects returned by the [Microsoft.BizTalk.Component.Interop.IPipelineContext.GetEventStream](/dotnet/api/microsoft.biztalk.component.interop.ipipelinecontext.geteventstream) method.  
  
 Messaging Event Streams are asynchronous and store tracking data first in the BizTalk MessageBox database. Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).  
  
 IPipelineContext is found in the [Microsoft.BizTalk.Component.Interop](/dotnet/api/microsoft.biztalk.component.interop) namespace. To use the API you must add the Microsoft.BizTalk.Pipeline (in microsoft.biztalk.pipeline.dll) to your project.  
  
## See Also  
 [OrchestrationEventStream](../core/orchestrationeventstream.md)   
 [Microsoft.BizTalk.Bam.EventObservation.EventStream](/dotnet/api/microsoft.biztalk.bam.eventobservation.eventstream)   
 [Microsoft.BizTalk.Component.Interop](/dotnet/api/microsoft.biztalk.component.interop)
