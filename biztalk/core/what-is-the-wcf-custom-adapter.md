---
description: "Learn more about: What Is the WCF-Custom Adapter?"
title: "What Is the WCF-Custom Adapter?"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# What Is the WCF-Custom Adapter?
The WCF-Custom adapter is used to enable the use of WCF extensibility components in BizTalk Server. The adapter enables complete flexibility of the WCF framework. It allows users to select and configure a WCF binding for the receive location and send port. It also allows users to set the endpoint behaviors and security settings.  
  
 The WCF-Custom adapter consists of two adapters—a receive adapter and a send adapter.  
  
 **WCF-Custom Receive Adapter**  
  
 You use the WCF-Custom receive adapter to receive WCF service requests through the bindings, service behavior, endpoint behavior, security mechanism, and the source of the inbound message body that you selected and configured in the transport properties dialog in the receive location. A receive location that uses the WCF-Custom receive adapter can be configured as one-way or request-response (two-way).  
  
 **WCF-Custom Send Adapter**  
  
 You use the WCF-Custom send adapter to call a WCF service through the typeless contract with the bindings, service behavior, endpoint behavior, security mechanism, and the source of the outbound message body that you selected and configured.  
  
 For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).  
  
## See Also  
 [Configuring the WCF-Custom Adapter](../core/configuring-the-wcf-custom-adapter.md)   
 [WCF Adapters](../core/wcf-adapters.md)
