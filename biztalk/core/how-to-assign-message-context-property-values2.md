---
title: "How to Assign Message Context Property Values2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 137f82ab-f301-465d-be78-a6e67971dd3b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Assign Message Context Property Values
To manage the JD Edwards OneWorld connection session from a BizTalk orchestration, you must add the reference to Microsoft.BizTalk.Adapters.JDEProperties.dll in your project. This assembly is located in %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.  
  
 After you reference this property schema, additional context properties are accessible to various BizTalk development tools, for example, the Message Assignment shape within the Orchestration Designer.  
  
 To access a context property, you specify one of the available context properties within the JD Edwards OneWorld namespace. To read a context property of a message received from a port bound to the Microsoft BizTalk Adapter for JD Edwards OneWorld, use the syntax, Message(JDE.Property), in an expression. Refer to JD Edwards OneWorld Session Management for a list of properties.  
  
 In BizTalk, messages are immutable.  
  
### To assign a message context property value  
  
1. Create a new message.  
  
2. Set the message content, for example, by assigning an existing message.  
  
3. Set the properties.  
  
   To assign context properties to a message destined to a send port that is bound to the Microsoft BizTalk Adapter for JD Edwards OneWorld, use the message assignment operator. Then, specify one of the available context properties within the JD Edwards OneWorld namespace.  
  
   The syntax is: `Message(JDE.Property) = value;`  
  
## See Also  
 [Using Message Context Properties](../core/using-message-context-properties2.md)   
 [About Session Management](../core/about-session-management1.md)   
 [Tutorial: Using the BizTalk Adapter for JD Edwards OneWorld](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-oneworld.md)