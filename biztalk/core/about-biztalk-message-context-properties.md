---
title: "About BizTalk Message Context Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc700e43-a44c-482b-b91c-9f1d997a486a
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# About BizTalk Message Context Properties
When a document is received by a BizTalk Server adapter, the adapter creates a BizTalk message for the document. The BizTalk message contains the document that was received as well as a message context. The message context is a container for various properties that are used by BizTalk Server when processing the document. Each property in the Message Context is composed of three things, a name, a namespace, and a value. For example, the following message context property describes the Interchange ID for a document:  
  
```  
<Property Name="InterchangeID" Namespace="http://schemas.microsoft.com/BizTalk/2003/system-properties" Value="{AC07BF30-2F1A-42B0-8390-191EF38BA839}"/>  
```  
  
 Message context properties are added to the message context throughout the lifetime of the message as it passes through BizTalk Server.  
  
 There are two different types of message context properties used by BizTalk as described below:  
  
## Property Fields  
 Property fields are message context properties that are used by the BizTalk Messaging Engine for purposes of document routing, for message tracking, and for evaluation in Orchestrations. You can explicitly elevate a field in a document to the message context as a Property field by editing the schema for the document in the BizTalk Server Schema Editor that is available in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. In order to write a field in a document to the message context as a property field, the document schema must have an associated property schema. Property fields are limited to 255 characters. The **IsPromoted** property of Property fields in the message context is set to **True**.  
  
## Distinguished Fields  
 Distinguished fields are message context properties that do not require a separate property schema and that are only accessible from Orchestrations. Distinguished fields cannot be used for routing or tracking. Since Distinguished fields do not require a separate property schema, the evaluation of Distinguished fields by the Orchestration engine consumes less overhead than the evaluation of Property fields by the Orchestration engine. The evaluation of Property fields requires an XPath query, the evaluation of Distinguished fields does not require an XPath query as the pipeline disassembler populates the Distinguished fields in the context and the orchestration engine reads the cached values. However, if the orchestration engine does not find the property in the context, it will then initiate an XPath query to find the value. Distinguished fields do not have a size limitation. The **IsPromoted** property of Distinguished fields in the Message context is set to **False**.  
  
## Summary of differences between Property Fields and Distinguished Fields  
 The table below summarizes the differences and similarities between Property fields and Distinguished fields:  
  
|**Attribute**|**Property Field**|**Distinguished Field**|  
|-------------------|------------------------|-----------------------------|  
|IsPromoted Property|True|False|  
|Size Limitation|255 Characters|No limit|  
|Used for Routing|Yes|No|  
|Used for Tracking|Yes|No|  
|Used in Orchestration|Yes|Yes|  
|Requires Property Schema|Yes|No|  
|Accessible by Pipelines and Ports|Yes|No|  
  
## See Also  
 [Ways to Use Message Content to Control Message Processing](../core/ways-to-use-message-content-to-control-message-processing.md)