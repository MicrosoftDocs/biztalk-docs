---
title: "How to Map Multiple Assemblies | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblies, tracking profiles"
  - "tracking profiles, mapping assemblies"
  - "assemblies, maps"
ms.assetid: 136f1943-9643-4551-8b5b-150c4b4bfebe
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Map Multiple Assemblies
BizTalk applications can consist of multiple assemblies in which the data items that a BAM activity references reside. The following procedure shows you how to map multiple assemblies to a tracking profile.  
  
### To map multiple assemblies  
  
1.  Open an existing tracking profile or create a new tracking profile. For more information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).  
  
2.  Click the **Select Event Source** button (located above the right pane in the Tracking Profile Editor).  
  
3.  Select the **Select Orchestration Schedule** menu item from the cascading menu.  
  
4.  Select the parent assembly from which to draw the orchestration by clicking the assembly containing the orchestration in the **Assembly Name** list box, and then click **Next**.  
  
5.  Select the orchestration that is the source for the data items in the **Orchestration Names** list box, and then click **OK**.  
  
6.  Select the data items in the right pane and drag them to the appropriate nodes in the activity in the left pane.  
  
7.  Repeat steps 2 through 6 to map additional assemblies.  
  
### To map the second assembly  
  
1.  Click the **Select Event Source**.  
  
2.  Select the **Select Orchestration Schedule** menu item from the cascading menu.  
  
3.  Select the next parent assembly from which to draw the orchestration by clicking the assembly containing the orchestration in the **Assembly Name** list box, and then click the **Next** button.  
  
4.  Select the orchestration that is the source for the data items in the **Orchestration Names** list box, and then click **OK**.  
  
5.  Select the data items in the right pane and drag them to the appropriate nodes in the activity in the left pane.  
  
## See Also  
 [How to Map Event Sources](../core/how-to-map-event-sources.md)   
 [Creating Tracking Profiles](../core/creating-tracking-profiles.md)