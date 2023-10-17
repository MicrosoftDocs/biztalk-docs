---
description: "Learn more about: Monitoring the Business Process Management Solution with BAM"
title: "Monitoring the Business Process Management Solution with BAM | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "process management solution tutorial, monitoring"
  - "monitoring, process management solutions"
ms.assetid: 7c5fde9d-6eef-41c9-979c-ac7e5a172812
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitoring the Business Process Management Solution with BAM
The solution monitors the steps in processing orders using the Business Activity Monitoring (BAM) API. The design of the business process splits activities among multiple stages. Through, the activities can be re-combined to create a sense of a continuous process. BAM also provides aggregate data so that you can know how long different back-ends are taking, how many orders have been completed, and other similar information.  
  
 Like the service-oriented solution, it uses the new **OrchestrationEventStream** object. For a discussion of the **OrchestrationEventStream** object, see "What Is the OrchestrationEventStream Object" in [Monitoring the Service Oriented Solution with BAM](../core/monitoring-the-service-oriented-solution-with-bam.md).  
  
 For general information about BAM, see [Using Business Activity Monitoring](../core/using-business-activity-monitoring.md). For information about the Tracking Profile Editor (TPE), see [Tracking Profile Editor](../core/tracking-profile-editor.md).  
  
## Wrapping the OrchestrationEventStream Object  
 Like the service-oriented solution, the business process management solution wraps the **OrchestrationEventStream** object. And, like the service-oriented solution, all of the methods are static so that the orchestrations do not need to create instances of objects in order to use the methods. This also means that the objects used in tracking do not have to be serialized and will not need to be saved (do not need to be serializable) if the engine dehydrates an orchestration. The business process management solution, however, wraps **OrchestrationEventStream** with several objects all derived from a single, abstract object.  
  
 The abstract class is **BasicActivity**. Although it is abstract, the class does not really serve as a template for derived classes. Rather, through its static methods, it provides a set of methods available without qualification in a derived class. This, in effect, gives you four default implementations of the methods. The four static methods are: **CreateActivityId**, **BeginActivity**, **UpdateActivity**, and **EndActivity**.  
  
 The class overloads the **BeginActivity** method. One version of it takes an activity name as a single argument, creates a GUID to use as the activity identifier, and then calls the version of itself that takes an activity name and an activity identifier, and then returns the activity identifier. This single argument version is useful for cases where an order might not have a unique identifier.  
  
 The **CreateActivityId** method takes a string and a unique identifier such as the request identifier and returns a string concatenating them with an underscore. This provides a unique activity identifier and is used extensively in the derived classes. The **BeginActivity**, **UpdateActivity**, and **EndActivity** methods call the **BeginActiviy**, **UpdateActivity**, and **EndActivity** methods of **OrchestrationEventStream**.  
  
 The solution derives classes from **BasicActivity** for the order broker (**CustomerOrderRequest**), order manager (**OrderManager**), and the processing stages (**ServiceOrderRequest**). Each of the classes corresponds to an activity. Each class provides a string for the activity name to be used in **CreateActivityId** to create the activity identifier as well as methods specialized for the activity milestones.  
  
 Because the order broker hands off the order and later receives a response, it includes a method to recover the activity identifier given to the request identifier of the order. This allows the business process to continue tracking the final elements of processing the order.  
  
> [!NOTE]
>  If you submit orders through the file facility rather than through the customer service web application, you need to add an identifier unique to each request.  
  
## See Also  
 [Developing a Business Process Management Solution](../core/developing-a-business-process-management-solution.md)
