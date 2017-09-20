---
title: "How to Configure the Parallel Actions Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Parallel Actions shape [Orchestration Designer], Terminate shape [Orchestration Designer]"
  - "Parallel Actions shape [Orchestration Designer], synchronizing data access"
  - "Parallel Actions shape [Orchestration Designer]"
  - "configuring [Orchestration Designer], Parallel Actions shapes"
  - "Parallel Actions shape [Orchestration Designer], branching"
  - "Parallel Actions shape [Orchestration Designer], about Parallel Actions shape"
  - "Terminate shape [Orchestration Designer], Parallel Actions shape [Orchestration Designer]"
  - "Parallel Actions shape [Orchestration Designer], configuring"
ms.assetid: 396d6182-f5dd-4aab-9edc-92efe236fd3e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Parallel Actions Shape
![](../core/media/ebiz-orch-paralactions.gif "ebiz_orch_paralactions")  
Parallel Actions shape  
  
> [!CAUTION]
>  If you place a **Terminate** shape inside a **Parallel Actions** shape, and the branch with the **Terminate** on it is run, the instance completes immediately, regardless of whether other branches have finished running. Depending on your design, results might be unpredictable in this case.  
  
## Synchronization of data access  
 It is possible that more than one branch of a **Parallel Actions** shape will attempt to access the same data. To avoid errors, place any shapes that access the data inside synchronized scopes. You can specify in the properties of a **Scope** shape that it is synchronized or not synchronized. For more information, see [Scopes](../core/scopes.md).  
  
#### To add a branch to a Parallel Actions shape  
  
1.  Right-click the **Parallel Actions** shape, and then click **New Parallel Branch**.  
  
     —Or—  
  
2.  Drag a new shape between two existing branches.  
  
> [!NOTE]
>  To remove a branch from a **Parallel Actions** shape, right-click the branch you want to remove, and then click **Delete**.