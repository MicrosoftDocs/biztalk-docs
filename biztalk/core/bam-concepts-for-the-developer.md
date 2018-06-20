---
title: "BAM Concepts for the Developer | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c26d0aed-821c-4e1f-9cc9-9375a2ba28de
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM Concepts for the Developer
As a BAM developer, you need to be familiar with important BAM concepts, such as activities, continuations, and references. You should also understand the differences between tracking and transactional processing.  
  
## What Is a BAM Activity?  
 A BAM activity is the definition of what data is interesting for an item in the business process (such as a single PO). It defines what columns are in the BAM database.  
  
 An instance of an activity represents a unit of work in the business, such as a purchase order or a loan application. An activity specifies a list of milestones (the history of the activity) and data of interest. An instance of an activity is manifested as a single row in the BAM Primary Import database. There is one and only one value for any data item for that instance of the activity.  
  
 An activity is used to show the milestones and data about this unit of work to the business end user, or information worker. For example, the activity defined in the BAM SDK sample contains milestones such as “Paid” and "Send," as well data of interest such as “Total Amount.”  
  
 BAM activities often map directly to a business process, although as a high-level abstraction an activity is independent of the actual implementation of your IT infrastructure.  
  
 Your job as a developer is to maintain this abstraction by exposing only the relevant milestones and data from the implementation in the context of a specific activity.  
  
## What Is a Continuation?  
 Continuations provide guidance to the BAM infrastructure about the following information:  
  
- The order in which events are expected to occur  
  
- A way to handle any change in the unique ID to which event items are correlated  
  
  For more information about Continuations and how they are used, see [Continuation and ContinuationID Nodes](../core/continuation-and-continuationid-nodes.md).  
  
## What Is a Reference?  
 A reference (also known as a related activity) specifies a relationship between an activity and some other item. Examples of items that can be related are another activity or a document location.  
  
> [!NOTE]
>  When you specify an activity as a related activity, the current activity is not, unlike a continuation activity, precluded from completing if the related activity has not completed.  
  
## Tracking and Transactional Processing  
 Writing code for BAM gives you control of the way data is tracked, that is, through tracking or transactional processing. By default, BAM assigns equal importance to tracking and processing. This means that if either the tracking function or the transaction process fails, neither is allowed to proceed. Nothing is recorded in the tracking database and the transaction is rolled back. This may not be the preferred method of tracking for your solution. By developing for BAM you can determine whether tracking or transactional processing takes precedence.  
  
 The following table describes the modes of tracking data in BAM.  
  
|Scenario|Descriptions|  
|--------------|------------------|  
|Tracking Over Processing|If the process succeeds, write tracking information.<br /><br /> If the process fails, write information about the failure.|  
|Processing Equal to Tracking|If either tracking or processing fails, roll back everything.|  
|Processing Over Tracking|If the process succeeds and the tracking function fails, continue processing.|