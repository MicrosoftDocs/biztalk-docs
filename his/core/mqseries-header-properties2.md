---
description: "Learn more about: MQSeries Header Properties"
title: "MQSeries Header Properties2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20fc6559-440f-4d0c-b532-983ebe00a502
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# MQSeries Header Properties
MQSC Adapter provides a set of context properties, specific to MQSeries, for use in your applications. You can use these properties in pipeline components, in your orchestrations and in filter expressions. For easy programmatic access, MQMD, MQXQH, MQCIH and MQIIH header structures can be directly accessed using these context properties.  
  
 All other MQSeries header structures (example: MQRFH) are supported by the MQSC Adapter. However, to access these headers, you need to do so with custom pipeline components and retrieve them from the body of the message. If you are setting them in the outbound message, then the pipeline component is responsible for ensuring that the message is constructed correctly.  
  
 To assign MQSeries context properties to a message destined to a send port that is bound to MQSC Adapter, use the message assignment operator and specify one of the available context properties in the MQSeries namespace.  
  
 The following is an example of setting the MQSeries MQMD_UserIdentifier property:  
  
 Message_2(MQSeries.MQMD_UserIdentifier) = "MeMyselfAndI";  
  
 You must obtain enumerated values from the C programming language header files included with the IBM MQSeries SDK. You can find these files in the Program Files\IBM\WebSphere MQ\Tools\c\include folder. These files define the values to use when setting or reading MQSeries context property values.  
  
 Hexadecimal string values are character strings representing binary values. They do not have a prefix such as 0x. They contain digits from 0 through 9 and letters from "a" through "f" or "A" through "F". The adapter ignores white space in them.  
  
 For more information about these properties, see the IBM WebSphere MQ documentation.  
  
## In This Section  
 [Message Descriptor Properties](../core/message-descriptor-properties2.md)  
  
 [Additional MQSeries Related Properties](../core/additional-mqseries-related-properties1.md)  
  
## See Also  
 [Context Properties](../core/context-properties1.md)
