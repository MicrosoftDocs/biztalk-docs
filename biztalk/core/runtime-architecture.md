---
title: "Runtime Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "runtime, architecture"
  - "architecture, runtime"
  - "runtime"
ms.assetid: feff9a84-f19b-44c9-8d05-8e6015bb1ef9
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Runtime Architecture
Before reviewing more detailed information about the various components in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], it is important that you have an understanding of how the components fit into the overall architecture of the product. The BizTalk Server runtime is built on a publish/subscribe architecture in which a message is published into the system, and then received by one or more active subscribers. Different flavors of this architecture exist, but the model implemented in BizTalk Server is often called *content-based publish/subscribe*.  
  
 In a content-based publish/subscribe model, subscribers specify the messages they want to receive using a set of criteria about the message. The message is evaluated at the time it is published, and all of the active subscribers with matching subscriptions (indicated by filter expressions), receive the message. As it applies to BizTalk Server, content-based is a bit of a misnomer, however, because the criteria used to build subscriptions do not have to come from the message content, and may include contextual information about the message as well. For details of the subscription mechanism, see [Publish and Subscribe Architecture](../core/publish-and-subscribe-architecture.md).  
  
 The sections that follow describe the various components of the BizTalk Server runtime architecture.  
  
## In This Section  
  
-   [The BizTalk Server Message](../core/the-biztalk-server-message.md)  
  
-   [Lifecycle of a Message](../core/lifecycle-of-a-message.md)  
  
-   [Processing the Message](../core/processing-the-message.md)  
  
-   [Request-Response Messaging](../core/request-response-messaging.md)  
  
-   [The Messaging Engine](../core/the-messaging-engine.md)  
  
-   [Entities](../core/entities.md)  
  
-   [Artifacts](../core/artifacts.md)  
  
-   [Enterprise Single Sign-On (SSO)](../core/enterprise-single-sign-on-sso.md)  
  
-   [Business Rules Engine](../core/business-rules-engine.md)  
  
-   [BizTalk Assemblies](../core/biztalk-assemblies.md)