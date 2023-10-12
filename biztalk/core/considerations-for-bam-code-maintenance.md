---
description: "Learn more about: Considerations for BAM Code Maintenance"
title: "Considerations for BAM Code Maintenance"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Considerations for BAM Code Maintenance

When you decide how to instrument your application to use BAM, you should consider the likelihood that requirements will change. If you call methods on one of the [Microsoft.BizTalk.Bam.EventObservation.EventStream](/dotnet/api/microsoft.biztalk.bam.eventobservation.eventstream) classes to write the data that is being monitored, you are essentially “hard-coding” the observation model into the application. If you need to change which data is being monitored, you will have to take the application offline, change the code, recompile the application, and then redeploy the updated application.  
  
 Alternatively, you can instrument your application by calling methods on the [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](/dotnet/api/microsoft.biztalk.bam.eventobservation.baminterceptor) class. The [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](/dotnet/api/microsoft.biztalk.bam.eventobservation.baminterceptor) class refers to a configuration file to determine which events and data to monitor. By using the [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](/dotnet/api/microsoft.biztalk.bam.eventobservation.baminterceptor) class, you can instrument your code once, and then change the data that is being monitored by updating the metadata, without having to take the application offline.  
  
## Instrumenting Your Application by Using the EventStream Object  
 This approach is simpler and applies when you are building a dedicated application with specific, well-known monitoring requirements. Before deciding to use this approach, you need to know the answers to the following questions:  
  
- What are the BAM milestones, and where in the code do they occur?  
  
- What data will be monitored, and when and where in the code is that data available?  
  
  If the answer to either of these questions is likely to change, you should consider instrumenting your application by using the [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](/dotnet/api/microsoft.biztalk.bam.eventobservation.baminterceptor) object instead.  
  
  When you follow this “hard-coded” approach, you simply call methods on the [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](/dotnet/api/microsoft.biztalk.bam.eventobservation.directeventstream), [Microsoft.BizTalk.Bam.EventObservation.BufferedEventStream](/dotnet/api/microsoft.biztalk.bam.eventobservation.bufferedeventstream), **MessagingEventStream** (from pipeline implementations) or **OrchestrationEventStream** (from orchestration implementations) class, depending on your requirements.  
  
## Instrumenting Your Application by Using the BAMInterceptor Object  
 This approach is better when:  
  
- You need to balance visibility of data with performance of the application, and you want to be able to control the data that is monitored at run time.  
  
- The application processes large XML messages, in which any data may eventually become important for monitoring.  
  
- It is unacceptable to stop the application and change the code to monitor different data.  
  
  In this approach, you instrument the application in a generic way by using the methods of the [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](/dotnet/api/microsoft.biztalk.bam.eventobservation.baminterceptor) class. By passing different configurations to the interceptor, you can change the data that BAM monitors.  
  
  You can use the Tracking Profile Editor (TPE) to change the data that BAM collects from a BizTalk orchestration.  
  
## See Also  
 [Using an Activity](../core/using-an-activity.md)   
 [What Is the BAM Interceptor?](../core/what-is-the-bam-interceptor.md)   
 [BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md)
