---
description: "Learn more about: What Is the WCF-CustomIsolated Adapter?"
title: "What Is the WCF-CustomIsolated Adapter?"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# What Is the WCF-CustomIsolated Adapter?
The WCF-CustomIsolated adapter is used to enable the use of WCF extensibility components in BizTalk Server with an isolated host. The adapter enables complete flexibility of the WCF framework. It allows users to select and configure a WCF binding for the receive location, and to specify the endpoint behaviors and security settings. This adapter can only be used by transports that are hosted in Internet Information Services (IIS).  
  
 The WCF-CustomIsolated adapter consists of a receive adapter only. You use the WCF-CustomIsolated receive adapter to receive WCF service requests through WCF bindings, service behavior, endpoint behavior, security mechanism, and the source of the inbound message body that you selected and configured for the receive location running in an isolated host. A receive location that uses the WCF-CustomIsolated receive adapter can be configured as one-way or request-response (two-way).  
  
 For more information about WCF receive adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).  
  
## See Also  
 [Configuring the WCF-CustomIsolated Adapter](../core/configuring-the-wcf-customisolated-adapter.md)   
 [WCF Adapters](../core/wcf-adapters.md)
