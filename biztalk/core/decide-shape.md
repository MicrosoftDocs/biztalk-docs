---
title: "Decide Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.decide"
ms.assetid: 3c3d25ce-8216-4617-a5b8-b481b39937a4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Decide Shape
The **Decide** shape represents a decision based on if/else logic. The shape always has a branch for the "if" statement and a branch for the "else" statement; you can add additional branches for "else if" statements as needed. You use the Expression editor to add a rule to each branch except the "else" branch. If the rule evaluates to true, the branch will be taken. Below the rule or "else" clause, a branch of a **Decide**shape can contain additional shapes, just like any other part of the orchestration.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Rule**|Right-click the rule to add a Boolean expression to determine whether this rule branch should be taken in your business process.|  
|**Rule** branch|Drag shapes onto this branch to specify any actions to take if the rule in this branch is satisfied.|  
|**Else** branch|Drag shapes onto this branch to specify any actions to take if none of the rules in other branches are satisfied.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|