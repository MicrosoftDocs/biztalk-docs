---
description: "Learn more about: Data Item Nodes"
title: "Data Item Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "definition files [BAM], data items"
  - "Data Item nodes [Tracking Profile Editor]"
  - "Tracking Profile Editor, node descriptions"
  - "Tracking Profile Editor, definition files [BAM]"
ms.assetid: 95856bfa-90e3-49d9-b55b-5f1b35a23f78
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Item Nodes
Data Item nodes exist in the activity definition file that the developer imports from the created observation model created by the business analyst. The Tracking Profile Editor (TPE) names them for the data items they are tracking, such as Customer Name. You then drop one or more data items from the Message Schema View onto the node that corresponds to Customer Name.  
  
## Working with data item nodes  
 When mapping Data Item nodes you should only track data items once per business process when that business process spans multiple tracking profiles. If you have a conditional path in your orchestration, you can select the data item from both paths because only one will run. However, you should not choose a shape inside a loop unless the values will be different for the data item with each iteration.  
  
## See Also  
 [How to Map Item Data](../core/how-to-map-item-data.md)   
 [TPE Activity View Nodes](../core/tpe-activity-view-nodes.md)
