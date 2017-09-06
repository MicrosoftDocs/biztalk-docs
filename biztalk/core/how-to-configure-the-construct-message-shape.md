---
title: "How to Configure the Construct Message Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Construct Message shape [Orchestration Designer], configuring"
  - "Construct Message shape [Orchestration Designer]"
  - "configuring [Orchestration Designer], Construct Message shapes"
  - "Construct Message shape [Orchestration Designer], about Construct Message shape"
ms.assetid: 8d052b4e-0873-4102-9462-6604423d0524
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Construct Message Shape
![](../core/media/ebiz-orch-constructmsg.gif "ebiz_orch_constructmsg")  
Construct Message shape  
  
 You specify the message variable that you want to construct, and make assignments to the message or its parts. All assignments to any given message must take place within the same Construct Message shape.  
  
 If you want to modify a property on a message that has already been constructed—such as a message that has been received—you must construct a new message instance by assigning the first to the second and then modifying the property on the new message instance; both the construction and modification occur within the same Construct Message shape.  
  
### To configure a Construct Message shape  
  
1.  In the Properties window, use the **Messages Constructed** property to specify which messages this shape will construct.  
  
2.  Add and configure one or more **Transform** or **Message Assignment** shapes inside the **Construct Message shape**.