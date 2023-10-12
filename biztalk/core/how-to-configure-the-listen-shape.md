---
description: "Learn more about: How to Configure the Listen Shape"
title: "How to Configure the Listen Shape"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure the Listen Shape
Listen actions enable applications to wait for one of several messages on one or more ports, or to stop waiting after a specified time-out interval, and branch based upon the results.  
  
 ![Image that represents the Listen shape.](../core/media/ebiz-orch-listen.gif "ebiz_orch_listen")  
Listen shape  
  
 You can add as many branches as you like. You can place any other shape below the initial **Receive** or **Delay** shape.  
  
 It is possible to use an activation receive in a **Listen** shape. If one branch of the **Listen** shape contains an activation receive, then all branches must contain activation receives, and no timeout can be used. The activation receive must be the first action in each branch.  
  
 You can use the **Listen** shape to branch orchestration flow based on the occurrence of one or more events. The first shape in each branch must be either a **Delay** or a **Receive** shape. The first branch that meets its condition—the occurrence of a time-out for a **Delay** shape or the receipt of a message for a **Receive** shape—will execute. You can add additional branches if needed.  
  
### To configure a Listen shape  
  
1.  Select a branch.  
  
2.  In the Properties window, specify the **Branch Type** property.  
  
     —Or—  
  
     Drag a **Delay** or **Receive** shape onto the branch.  
  
### To add a branch to a Listen shape  
  
-   Right-click the **Listen** shape and then click **New Listen Branch**.  
  
    > [!NOTE]
    >  To remove a branch from a **Listen** shape, right-click the branch you want to remove, and then click **Delete**.
