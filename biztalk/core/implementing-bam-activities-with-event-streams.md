---
title: "Implementing BAM Activities with Event Streams | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "activities [BAM], about activities"
  - "activities [BAM]"
  - "BAM, activities"
ms.assetid: 94e6d9dd-93c3-4ab0-9de7-a860dd1e3406
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implementing BAM Activities with Event Streams
A BAM activity represents a unit of work in the business, such as purchase order or loan application. The activity shows the history (milestones) and data about this unit of work to the business end user, or information worker. For example, a loan application activity might contain milestones such as “Loan approved” and data such as “Applicant name” and “Loan amount.” BAM activities often map directly to a business process, although as a high-level abstraction an activity is independent of the actual implementation of your IT infrastructure.  
  
 Your job as a developer is to maintain this abstraction by exposing only the relevant milestones and data from the implementation in the context of a specific activity. For a code sample that demonstrates the use of an activity, see [BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md).  
  
## In This Section  
  
-   [Why Write Code For BAM?](../core/why-write-code-for-bam.md)  
  
-   [BAM Concepts for the Developer](../core/bam-concepts-for-the-developer.md)  
  
-   [Overview of the BAM Development Process](../core/overview-of-the-bam-development-process.md)  
  
-   [EventStream Classes](../core/eventstream-classes.md)  
  
-   [Using an Activity](../core/using-an-activity.md)  
  
-   [Activity Relationships](../core/activity-relationships.md)  
  
-   [Activity Continuation](../core/activity-continuation.md)  
  
-   [Looping Activities](../core/looping-activities.md)  
  
-   [Instrumenting a Solution: Step-by-Step API Usage](../core/instrumenting-a-solution-step-by-step-api-usage.md)