---
description: "Learn how to read the context property of a message received from a port bound to the Microsoft BizTalk Adapter for JD Edwards EnterpriseOne and assign property values to it."
title: "How to Assign Message Context Property Values1"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Assign Message Context Property Values

To manage the JD Edwards EnterpriseOne Adapter connection session from a BizTalk orchestration, you must add the reference to Microsoft.BizTalk.Adapters.JDEProperties.dll in your project. This assembly is located in %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.  
  
 After you reference this property schema, additional context properties are accessible to various BizTalk development tools, for example, the Message Assignment shape within the Orchestration Designer.  
  
 To access a context property, you specify one of the available context properties within the JD Edwards EnterpriseOne namespace. To read a context property of a message received from a port bound to the Microsoft BizTalk Adapter for JD Edwards EnterpriseOne, use the syntax, Message(JDE.Property), in an expression. Refer to JD Edwards EnterpriseOne Adapter Session Management for a list of properties.  
  
 In BizTalk, messages are immutable.  
  
### To assign context property value  
  
1. Create a new message.  
  
2. Set the message content, for example, by assigning an existing message.  
  
3. Set the properties.  
  
   To assign context properties to a message destined to a send port that is bound to the Microsoft BizTalk Adapter for JD Edwards EnterpriseOne, use the message assignment operator. Then specify one of the available context properties within the JD Edwards EnterpriseOne namespace.  
  
   The syntax is: `Message(JDE.Property) = value;`  
  
## See Also  
 [Using Message Context Properties](../core/using-message-context-properties1.md)   
 [About Session Management](../core/about-session-management2.md)   
 [Tutorial: Using the BizTalk Adapter for JD Edwards EnterpriseOne](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-enterpriseone.md)
