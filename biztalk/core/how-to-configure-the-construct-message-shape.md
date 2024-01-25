---
description: "Learn more about: How to Configure the Construct Message Shape"
title: "How to Configure the Construct Message Shape"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure the Construct Message Shape
![Image that represents the Construct Message shape.](../core/media/ebiz-orch-constructmsg.gif "ebiz_orch_constructmsg")  
Construct Message shape  
  
 You specify the message variable that you want to construct, and make assignments to the message or its parts. All assignments to any given message must take place within the same Construct Message shape.  
  
 If you want to modify a property on a message that has already been constructed—such as a message that has been received—you must construct a new message instance by assigning the first to the second and then modifying the property on the new message instance; both the construction and modification occur within the same Construct Message shape.  
  
### To configure a Construct Message shape  
  
1.  In the Properties window, use the **Messages Constructed** property to specify which messages this shape will construct.  
  
2.  Add and configure one or more **Transform** or **Message Assignment** shapes inside the **Construct Message shape**.
