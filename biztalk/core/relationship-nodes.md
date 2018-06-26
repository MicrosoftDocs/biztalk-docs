---
title: "Relationship Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "definition files [BAM], relationships"
  - "definition files [BAM], Tracking Profile Editor"
  - "Relationship nodes [Tracking Profile Editor]"
  - "activities [BAM], relationships"
  - "activities [BAM], Tracking Profile Editor"
  - "Tracking Profile Editor, node descriptions"
  - "Tracking Profile Editor, definition files [BAM]"
ms.assetid: 74090133-24d1-4aba-a4fc-f12d19c881fb
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Relationship Nodes
Relationship folders are used whenever an activity definition file contains more than one activity. The names of the folders match the name of the associated activity. You form the link by matching the name of the relationship folder to the activity ID of the related activity and by matching the values for the data items. You define each relationship using a separate node.  
  
## Working with Relationship nodes  
 To indicate the unique instance identifier that links the data item between activities:  
  
- Map a data item to the ActivityId node of the main orchestration.  
  
- Drag and drop a data item with the same name as above to the Relationship node in the related activity. The Relationship node has the same name as the Activity node of the main activity.  
  
  For example, in the sample scenario, there could be a related but separate business process represented in an orchestration called RefinanceOrchestration. That orchestration could contain a LoanRefinance Activity node, a Refinance ActivityID, and orchestration shapes such as Receive Appraisal Request. The Relationship node and relationship ID, however, could be LoanID, indicating the link to the original LoanProcess activity.  
  
## See Also  
 [TPE Activity View Nodes](../core/tpe-activity-view-nodes.md)