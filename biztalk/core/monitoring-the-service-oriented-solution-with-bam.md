---
description: "Learn more about: Monitoring the Service Oriented Solution with BAM"
title: "Monitoring the Service Oriented Solution with BAM"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Monitoring the Service Oriented Solution with BAM
The solution monitors activity in all versions of the **CustomerService** orchestration using the Business Activity Monitoring (BAM) API. More specifically, it uses the new **OrchestrationEventStream** object.  
  
## What is the OrchestrationEventStream Object?  
 The new **OrchestrationEventStream** object enables tracking and monitoring from orchestrations. The information captured is transactionally consistent with the orchestration state. For example, if the orchestration host instance restarts in the middle of executing the orchestration, the orchestration instance restarts from the last persistence point of the instance. The **OrchestrationEventStream** class ensures that the captured data is transactionally consistent with the orchestration instance's last persistence point. All of the **OrchestrationEventStream** methods are static so that your orchestration does not need to create an instance of it.  
  
> [!NOTE]
>  To use the **OrchestrationEventStream** object, you need to add references to the **Microsoft.BizTalk.Bam.XLANGs** and **Microsoft.BizTalk.Bam.EventObservation** assemblies. Although the **OrchestrationEventStream** object is in the **Microsoft.BizTalk.Bam.EventObservation** namespace, it resides in the **Microsoft.BizTalk.Bam.XLANGs** assembly.  
  
 Although the Tracking Profile Editor (TPE) is the preferred way of using BAM, TPE cannot capture the orchestration variable values, nor can it handle custom objects. The solution uses the BAM API to overcome these limitations.  
  
 For general information about BAM, see [Using Business Activity Monitoring](../core/using-business-activity-monitoring.md). For information about the Tracking Profile Editor (TPE), see [Tracking Profile Editor](../core/tracking-profile-editor.md).  
  
## Wrapping the OrchestrationEventStream Object  
 The service oriented solution wraps the **OrchestrationEventStream** class with the **ServiceLevelTracking** class. The **ServiceLevelTracking** class provides application-specific milestone methods and hides some of the details of using **OrchestrationEventStream**.  
  
 As in **OrchestrationEventStream**, all the methods of **ServiceLevelTracking** are static. Thus, the orchestration or custom component does not need to create an instance of it. The method that begins tracking an activity, **TrackingBeginRequest**, returns a unique activity instance ID. All subsequent tracking events must be associated with this activity instance ID in order to capture the service level data correctly, because it is unique to the instance of the **CustomerService** orchestration.  
  
## See Also  
 [Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md)   
 [Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md)
