---
title: "How to Map Item Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data extraction"
  - "orchestrations, data extraction"
  - "orchestrations, tracking profiles"
  - "tracking profiles, orchestrations"
  - "tracking profiles, data extraction"
ms.assetid: ae8b395e-152a-4e08-af31-3c9276f52711
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Map Item Data
You map item data to define the data extraction from an orchestration.  
  
> [!NOTE]
>  You must be certain to map data type values that are compatible with the activity items when creating tracking profiles. If the data types are not compatible you will receive a BAM runtime error.  
  
> [!NOTE]
>  When mapping milestones, such as Date/Time stamps, the data being mapped must conform to the SQL string representation of a date time stamp. DateTime data in the XML DateTime format that is formatted in the following manner, YYYY-MM-DDTHH:MM:SS.mmm-HH:MM, is not supported.  
>   
>  For example, the following date string, 1999-05-31T13:20:00.000-05:00, is not supported.  
  
## Prerequisites  
 Deployed BAM activity definitions and orchestrations that you will connect.  
  
### How to map item data  
  
1.  Open an existing tracking profile or create a new tracking profile. For more information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).  
  
2.  In the scenario, an activity definition called LoanProcessBamDef is imported. It contains the **LoanProcess** activity node, with a customer's **SSN** as an ActivityID. For more information, see [Activity and ActivityID Nodes](../core/activity-and-activityid-nodes.md).  
  
3.  Ensure that every activity has an ActivityID or a ContinuationID data item, such as customer SSN, to track.  
  
4.  Map orchestration actions to the appropriate business events folder to indicate the event to track. For example, in a loan processing scenario the following items, among others, would be dragged under the **LoanProcess** activity folder:  
  
    -   **LoanApplicationReceived**  
  
    -   **CreditHistoryRequest**  
  
    -   **CreditHistoryResponse**  
  
## See Also  
 [Data Item Nodes](../core/data-item-nodes.md)   
 [Creating Tracking Profiles](../core/creating-tracking-profiles.md)