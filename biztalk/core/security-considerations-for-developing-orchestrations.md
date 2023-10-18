---
description: "Learn more about: Security Considerations for Developing Orchestrations"
title: "Security Considerations for Developing Orchestrations"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Security Considerations for Developing Orchestrations
When designing your orchestrations, you should consider potential security issues.  
  
## Avoid subscriptions based on content from untrusted messages  
 To ensure that a low-privilege message does not initiate an orchestration instance that could potentially create subscriptions based on the message content or context, it is highly recommended that your orchestrations do not create their message subscriptions based on the content or context of a message that is not trusted.  
  
 For information about security in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Securing BizTalk Server](../core/securing-biztalk-server.md).  
  
## See Also  
 [Creating Orchestrations](../core/creating-orchestrations.md)   
 [About Orchestrations](../core/about-orchestrations.md)
