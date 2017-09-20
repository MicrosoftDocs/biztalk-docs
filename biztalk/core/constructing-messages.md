---
title: "Constructing Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, messages"
  - "multi-part message types"
  - "messages, modifying"
  - "multi-part message types, about multi-part message types"
  - "modifying, messages"
  - "messages, creating"
ms.assetid: c9fc1e97-ff53-42e2-848c-6c8fae7c9122
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Constructing Messages
You construct a message any time that you introduce a message into your orchestration, either by receiving it or by assigning values to a message variable. Any message that you construct must have a message type, so that the runtime engine has a complete description of the object that it is working with. The multi-part message type can be user-defined, it can be a .NET class, or it can be a schema. You can construct messages in various ways: you can invoke a .NET class to create a message, assign one message to another, or use a transform to map certain values within a message to values within another message. Messages are also constructed by a receive action or when your orchestration accepts a message as a parameter.  
  
> [!NOTE]
>  A multi-part message type does not necessarily contain multiple parts; it might contain just one.  
  
> [!IMPORTANT]
>  Messages are immutable in BizTalk; that is, once you have constructed it, you cannot modify the original. If you need to make a change, you must construct a new copy of the message and assign values to it appropriately.  
  
## In This Section  
 [How to Configure the Construct Message Shape](../core/how-to-configure-the-construct-message-shape.md)  
  
 [How to Configure the Message Assignment Shape](../core/how-to-configure-the-message-assignment-shape.md) 
  
 [How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md) 
  
 [Message References in Message Assignment Shape](../core/message-references-in-message-assignment-shape.md)  
  
 [Message References in User Code](../core/message-references-in-user-code.md)  
  
 [Using XPaths in Message Assignments](../core/using-xpaths-in-message-assignments.md)  
  
 [Using Non-Canonical XPaths in Message Assignments](../core/using-non-canonical-xpaths-in-message-assignments.md)  
  
 [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md)  
  
 [Appending Nodes to Messages in User Code](../core/appending-nodes-to-messages-in-user-code.md)  
  
## See Also  
 [Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md)