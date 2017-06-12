---
title: "Construct Message Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.message.construct"
ms.assetid: bd57a22d-d6ee-41da-a0f8-f28c61af64f3
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Construct Message Shape
Use the **Construct Message** shape to construct a new instance of a multipart message type. It must contain either a **Message Assignment** shape or a **Transform** shape, and can contain any number of either, but no other shapes. You specify the message variable that you want to construct, and make assignments to the message or its parts. All assignments to any given message must take place within the same **Construct Message** shape. If you want to modify a property on a message that has already been constructed—such as a message that has been received—you must construct a new message instance by assigning the first to the second and then modifying the property on the new message instance; both the construction and modification occur within the same **Construct Message** shape.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Messages Constructed** property|From the drop-down list, select the names of any messages that will be constructed in this shape.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Construct Message Shape](../core/how-to-configure-the-construct-message-shape.md)