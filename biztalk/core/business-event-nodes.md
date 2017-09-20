---
title: "Business Event Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "events, Tracking Profile Editor"
  - "events, date specific"
  - "events, time specific"
  - "Tracking Profile Editor, node descriptions"
  - "Business Event nodes [Tracking Profile Editor]"
  - "Tracking Profile Editor, events"
ms.assetid: 177bc3c4-e762-42fe-80bc-edede5cd4fcd
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Business Event Nodes
Business Event or milestone nodes define events that are date- or time-specific. Pre-defined business event and milestone folders exist in the activity definition you import from the business end user, and you cannot delete them without reimporting the activity definition file.  
  
## Working with business event nodes  
 You can drag shapes from the orchestration into the Business Events folder to track those events as the execution of the shapes is completed.  
  
 TPE uses the name of the shape for the name of the event folder, and this folder will have a unique icon. For example, in the sample loan-process scenario, TPE names them according to the event, such as Approved or Denied. You should only track business events once per business process when that business process spans multiple tracking profiles. If you have a conditional path in your orchestration, you can select the business event from both paths, as only one will ever execute. You should not select a shape inside a loop.  
  
> [!NOTE]
>  While you cannot delete folders without reimporting the activity definition, you can delete shapes (events).  
  
## See Also  
 [TPE Activity View Nodes](../core/tpe-activity-view-nodes.md)