---
title: "How to Create a Continuation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "activities, relating events"
  - "tracking profiles, relating events"
  - "continuations, tracking profiles"
  - "activities, continuations"
  - "events, relating"
  - "orchestrations, business events"
  - "tracking profiles, updating"
  - "activities, tracking profiles"
  - "tracking profiles, continuations"
  - "tracking profiles, connecting activities"
ms.assetid: 31d6fc24-676e-418c-8e78-1a46b045905d
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Continuation
You create continuations to indicate which business events in one or more orchestrations are related by constructing connected activities.  
  
> [!IMPORTANT]
>  Updating a tracking profile can impact activity instances in progress if the activity includes a BAM continuation. Specifically, if the update to the tracking profile specifies a downstream interception of data for an activity item already recorded, it is possible that the original value will be overwritten. In essence, any single event stream will not be affected by the application of tracking profile updates because each stream object is tied to the specific version of the profile which was in place at the time the activity/stream started.  However, because continuations are the means of correlating multiple event streams, streams not yet begun at the time of a profile update will pick up the changes in the update, thus introducing the possible data overwrite described.  
  
> [!NOTE]
>  You can create continuations with orchestrations that do not process messages. You can obtain the same functionality as you can for orchestrations that do process messages by passing parameters in execution calls between orchestrations and by using BAM APIs to process the continuation.  
  
## Prerequisites  
 To perform this procedure, you must have deployed BAM activity definitions and orchestrations that you will connect to.  
  
### To create a continuation  
  
1.  Open an existing tracking profile or create a tracking profile. For information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).  
  
2.  Identify a *continuation token,* which is a piece of unique information that is available to both activities. For example, if a **CreditHistory** activity is activated by a message sent from a **LoanProcess** activity within an **EquityLoan**orchestration, the SSN field of the message can be used as a continuation token because it is common to both activities.  
  
3.  Right-click the activity and then select **New Continuation** to create a continuation (CreditHistory). Name the continuation node you just created.  
  
4.  From the Orchestration Schedule View, select the continuation token you chose in step 2, such as SSN (in this case from the Send action) and drop it into the continuation node you created in step 3.  
  
5.  Right-click the activity and select **New ContinuationID** to create a Continuation ID node. Name it using the name you chose in step 3, and drop it in the node that contains the corresponding data item (in this case, SSN from the Receive action).  
  
6.  On the **File**menu, click **Save As**to save the tracking profile as a .btt file to the BizTalk Management database and to avoid overwriting any existing .btt file.  
  
## See Also  
 [Continuation and ContinuationID Nodes](../core/continuation-and-continuationid-nodes.md)   
 [Creating Tracking Profiles](../core/creating-tracking-profiles.md)