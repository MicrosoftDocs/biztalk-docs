---
description: "Learn more about: Creating Schemas"
title: "Creating Schemas"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Creating Schemas
You can use BizTalk Editor to create two types of schemas: message schemas and property schemas.  
  
> [!NOTE]
>  There are several types of message schemas, including XML message schemas, flat file message schemas, and envelope schemas.  
  
 Message schemas define the structure and constrain the content of messages that you expect to send to, and receive from, your trading partners or applications. Message schemas are the most common types of schemas that you will use with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can create XML message schemas for both business documents and the envelopes used to contain them, and through the use of the Flat File Extension to BizTalk Editor, it can create flat file message schemas, including schemas for headers, bodies and trailers.  
  
 Property schemas are a special type of schema. Property schemas provide a validation template for field and/or record data that is promoted from within an instance message into what is known as the message context. The purpose of property schemas is to provide a formal, strongly typed definition of the data to be promoted at run time.  
  
 Property promotion provides a centralized mechanism for pulling key pieces of information, defined by you, from within an instance message and making it more easily accessible to BizTalk Server components that are handling the message as it passes through BizTalk Server. One common use of promoted properties is in matching a message instance to a subscription, allowing the message to be properly routed for processing.  
  
 This section describes the ways in which you can create different types of schemas within BizTalk Server, and presents related subjects that pertain to multiple types of schemas.  
  
## In This Section  
  
-   [Managing Schemas Within Projects](../core/managing-schemas-within-projects.md)  
  
-   [Managing the Nodes Within a Schema](../core/managing-the-nodes-within-a-schema.md)  
  
-   [Promoting Properties](../core/promoting-properties.md)
