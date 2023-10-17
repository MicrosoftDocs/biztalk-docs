---
description: "Learn more about: Security Considerations for Developing Orchestrations"
title: "Security Considerations for Developing Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, orchestrations"
  - "messages, subscriptions"
  - "orchestrations, security"
  - "messages, security"
ms.assetid: a29b2018-4a8f-49ad-a817-6f279db3f801
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security Considerations for Developing Orchestrations
When designing your orchestrations, you should consider potential security issues.  
  
## Avoid subscriptions based on content from untrusted messages  
 To ensure that a low-privilege message does not initiate an orchestration instance that could potentially create subscriptions based on the message content or context, it is highly recommended that your orchestrations do not create their message subscriptions based on the content or context of a message that is not trusted.  
  
 For information about security in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Securing BizTalk Server](../core/securing-biztalk-server.md).  
  
## See Also  
 [Creating Orchestrations](../core/creating-orchestrations.md)   
 [About Orchestrations](../core/about-orchestrations.md)
