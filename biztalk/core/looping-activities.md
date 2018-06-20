---
title: "Looping Activities | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "activities [BAM], looping activities"
  - "activities [BAM], orchestrations"
  - "orchestrations, looping"
  - "orchestrations, activities"
ms.assetid: fb40fdd0-ac8f-486a-b3d0-9d2200a87cda
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Looping Activities
Looping activities refers to actions that loop within an orchestration. It is possible to capture the events from actions that loop within an orchestration. To do this, you create another activity and map all of the new activity milestones and data inside the loop. This is necessary because the data processing in the loop will occur more than once per scheduled execution. The following figure shows an example of this situation.  
  
 ![](../core/media/handlingloops2.gif "handlingloops2")  
  
 As shown in the figure, if you have a Purchase Order with multiple Line Items that process in a loop, questions like "Which purchase orders have item prices of $100?" are ambiguous. Unambiguous questions are:  
  
- Which purchase orders have line items with a price of $100?  
  
- Which purchase orders have Total/Min/Max item prices of $100?  
  
  Creating unambiguous questions requires thinking of the line items as something separate from the purchase order. In the Tracking Profile Editor, the root activity (for example, a purchase order) maps to all actions outside the loop. The child activity (for example, line item) maps to the actions inside the loop.  
  
  You need to use a payload item as ActivityID for the root activity. Have this payload item available in some of the messages inside the loop. Map the activity to the Relationship node that displays under the child activity and name it as the root activity.  
  
## See Also  
 [Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md)