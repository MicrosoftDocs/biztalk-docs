---
title: "Continuation and ContinuationID Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "continuation tokens"
  - "Continuation nodes [Tracking Profile Editor]"
  - "Tracking Profile Editor, node descriptions"
  - "BAM, correlating activities"
  - "activities, linking"
  - "activities, continuation tokens"
  - "ContinuationID nodes [Tracking Profile Editor]"
ms.assetid: aa050660-66f7-4084-b6bf-b9319ce625af
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Continuation and ContinuationID Nodes
Continuations provide guidance to the BAM infrastructure about the following information:  
  
- The order in which events are expected to occur  
  
- A way to handle any change in the unique ID to which event items are correlated  
  
  To state this another way, continuations define the transfer of this information between contributors to an activity. A transfer occurs in the following situations:  
  
- There is a change in the ActivityID between the time an activity begins and ends. For example, you have two related messages such as a Purchase Order number and Sales Order number. Each has a unique number assigned to it, such as 123456 for the Purchase Order number and 987654 for Sales Order number. You would use a continuation to equate the unique identifiers for the Purchase Order and the Sales Order so that events can be correlated to the common activity regardless of which unique identifier is associated with the incoming events.  
  
- You have a transition from one run-time environment to another. For example, in a scenario where you have an application that supplies a purchase order to a BizTalk Server messaging pipeline, which then invokes an orchestration, and the orchestration then passes control to an application that sends a shipping notice, you have two environment transitions: from a messaging pipeline to a an orchestration and from an orchestration to a messaging pipeline.  
  
  An important point to remember when selecting a property to use for your continuation is that the properties must be mapped from the same context.  
  
  For example, if you have the propertiesy Message.InterchangeID and servicecontext.InterchangeID it might appear that you could use the InterchangeID to create your continuation. If the messages come from different contexts you cannot use the InterchangeID (or other property) to reliably create a continuation.  
  
## Working with Continuation nodes  
 The Continuation node contains data items that indicate a unique instance ID, also called a *continuation token*. By using the continuation token, developers can link to other activities using the ContinuationID node.  
  
 There are three basic scenarios in which Continuation and ContinuationID nodes are used:  
  
- Orchestration to orchestration  
  
- Orchestration to BizTalk solution  
  
- BizTalk solution to orchestration  
  
  In the orchestration scenario the TPE must define a Continuation node, and a ContinuationID node, and the nodes must have the same name in order for BAM to correlate the activities.  
  
  In the orchestration to BizTalk solution scenario, you use the TPE to define a Continuation node and the developer creates a solution that uses the BAM API to handle the destination portion of the continuation..  
  
  In the BizTalk solution to orchestration, the developer uses the BAM API to supply the origination of the continuation pair and you use TPE to define a ContinuationID node.  
  
> [!NOTE]
>  Two-way ports can operate in either direction, which means that interception of data that passes through the ports can, depending on the behavior of the BizTalk solution, require enabling of a continuation. For example, if the activity records “PortEndTime” for activation of a BizTalk Server messaging port in either direction (if the item names are, for example, “MessageReceived” and “MessageSent,” in that order), you need to create a continuation between them. A continuation is required any time more than one event stream contributes to a BAM activity, and there are distinct event streams per implementation touch point (such as BTS Messaging in, BTS Messaging out, Orchestration, custom applications, and Web services).  
  
## See Also  
 [How to Create a Continuation](../core/how-to-create-a-continuation.md)   
 [TPE Activity View Nodes](../core/tpe-activity-view-nodes.md)