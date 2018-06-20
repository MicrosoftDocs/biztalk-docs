---
title: "Orchestration Schedule View | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Orchestration view [Tracking Profile Editor]"
  - "orchestrations, Tracking Profile Editor"
  - "Tracking Profile Editor, Orchestration view"
  - "Tracking Profile Editor, orchestrations"
ms.assetid: b3e0014b-000e-4f58-9f70-d331d78e487e
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Orchestration Schedule View
The Orchestration View displays the steps by which BAM transacts the business process contained within the selected orchestration. The view is located on the right pane of the Tracking Profile Editor (TPE) user interface.  
  
## Working with the Orchestration Schedule view  
 You select your orchestration view by clicking the **Select Event Source** button and clicking the **Select Orchestration Schedule** menu item. You then choose an assembly from which to select an orchestration. Once you select the orchestration, you can drag orchestration shapes that represent orchestration constructs or actions from the orchestration into the business milestone folders in the activity view to do the following:  
  
- Create a mapping between the low-level implementation of the business process and the BAM activity.  
  
- Indicate the time stamp to track when the associated underlying construct or action has completed.  
  
  Right-clicking a shape in the orchestration schedule view opens a context menu that allows you to view any message payloads, context properties, or message properties that are associated with the shape.  
  
  For an explanation of the displayed in the Orchestration View, see [Orchestration Shapes](../core/orchestration-shapes.md).  
  
  The list of available orchestrations can be extensive. If you know part of the name of the orchestration for which you are searching, you can type it in the **In String** text box and click the **Search** button. This will select only those orchestrations that contain the partial string you have entered.  
  
## See Also  
 [What Is the Source Event View?](../core/what-is-the-source-event-view.md)   
 [Tracking Profile Editor](../core/tracking-profile-editor.md)