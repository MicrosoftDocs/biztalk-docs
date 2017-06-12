---
title: "Message Context Properties in BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message context properties, accessing"
  - "message context properties, BizTalk Server"
ms.assetid: 163ac2cf-0e2d-4780-b398-baa825f92b00
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Context Properties in BizTalk Server
To access TIBCO Enterprise Message System message descriptor fields from a BizTalk Server orchestration, you must add a reference to **Microsoft.BizTalk.Adapters.TibcoEMSProperties.dll** to your project. This assembly is located in **\<TIBCO EMS_Adapter_installation_directory>\bin**. After you reference this TIBCO EMS property schema, additional context properties can be accessed by various BizTalk Server development tools (for example, the message assignment shape in the orchestration designer).  
  
## Accessing Context Properties  
 To access a context property, you specify one of the available context properties in the TIBCO EMS namespace. To read the context property of a message received from a port bound to BizTalk Adapter for TIBCO EMS, use the following syntax in an expression:  
  
```  
Message(TibcoEMS.Property)  
```  
  
 For more information, see [TIBCO Enterprise Message Service Message Descriptor Properties](../core/tibco-enterprise-message-service-message-descriptor-properties.md).  
  
 In BizTalk Server, messages are immutable. Therefore, to assign a message context property value, you create a new message, set the message content (possibly by assigning an existing message), and then set the properties that you need.  
  
 To assign TIBCO EMS context properties to a message destined to a send port that is bound to BizTalk Adapter for TIBCO EMS, use the message assignment operator and specify one of the available context properties in the TIBCO EMS namespace. The syntax is as follows:  
  
```  
Message(TibcoEMS.Property) = value;  
```  
  
## See Also  
 [Message Context Properties](../core/message-context-properties2.md)