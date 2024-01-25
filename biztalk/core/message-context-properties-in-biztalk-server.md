---
title: "Use TIBCO EMS message Context Properties"
description: Use the TIBCO Enterprise Message System message descriptor fields in a BizTalk Server orchestration
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Message Context Properties in TIBCO EMS

## TibcoEMSProperties.dll
To access TIBCO Enterprise Message System message descriptor fields from a BizTalk Server orchestration, you must add a reference to **Microsoft.BizTalk.Adapters.TibcoEMSProperties.dll** to your project. This assembly is located in **\<TIBCO EMS_Adapter_installation_directory\>\bin**. After you reference this TIBCO EMS property schema, additional context properties can be accessed by various BizTalk Server development tools (for example, the message assignment shape in the orchestration designer).  
  
## Access context Properties  
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
  
## Next steps
-   [TIBCO EMS Message Descriptor properties & values](../core/tibco-enterprise-message-service-message-descriptor-properties.md)  
  
-   [Tutorial: Use Message Context Properties](../core/tutorial-using-message-context-properties.md)